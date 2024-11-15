Android <mark style="background: #AD21D9;">ROOM</mark> is for Storing Permanent data

### <mark style="background: #AD21D9;">Annotations</mark>

Annotations provide information about your program (classes, methods, fields) accessible to processing by <mark style="background: #AD21D9;">external tools</mark>.

Similar to <mark style="background: #AD21D9;">modifier</mark> (e.g. public or static), should appear on own line before other modifiers.

Indicated by an <mark style="background: #AD21D9;">@</mark> character followed by name of annotation type.

### <mark style="background: #AD21D9;">Example:</mark>

Keeping track of <mark style="background: #AD21D9;">code reviews</mark>

Annotations allow you to provide review information e.g. reviewer name, date

```Kotlin
@Reviewed(reviewer = "Abubakr Siddig", date = 20231024)
class MyClass {
	// ...
}
```

Values are supplied for elements of annotation type e.g. reviewer = “Abubakr Siddig”

Tool can then automatically <mark style="background: #AD21D9;">extract</mark> these values from either source file, or (more often) compiled class file. e.g. determine whether a class has been reviewed since it was last <mark style="background: #AD21D9;">modified</mark>.

# <mark style="background: #FF5582A6;">SLIDE 6:</mark>

### <mark style="background: #AD21D9;">Overview:</mark>

ROOM is a robust SQL <mark style="background: #AD21D9;">object</mark> mapping library

Generates <mark style="background: #AD21D9;">SQLite</mark> Android code

Provides a <mark style="background: #AD21D9;">simple</mark> API for your database

Offers layer over SQLite for smooth database access while harnessing full power of SQLite.

Apps that handle reasonable amounts of structured data can benefit greatly from storing that data <mark style="background: #AD21D9;">locally</mark>.

Most common use case is <mark style="background: #AD21D9;">caching</mark> relevant pieces of data i.e. when device cannot access network, user can still browse content <mark style="background: #AD21D9;">offline</mark>

User-initiated content changes <mark style="background: #AD21D9;">synced</mark> to server after device is back online.

As ROOM takes care of these concerns for you, it is highly <mark style="background: #AD21D9;">recommended</mark> using ROOM instead of SQLite.

### <mark style="background: #AD21D9;">Modern Android:</mark>

# <mark style="background: #FF5582A6;">SLIDE 10:</mark>

### <mark style="background: #AD21D9;">Components:</mark>

<mark style="background: #AD21D9;">3 major components in ROOM:</mark>
- <mark style="background: #AD21D9;">Entity</mark> Represents table within database.
- <mark style="background: #AD21D9;">Database</mark> Contains database holder and serves as main access point for underlying connection to app's stored, relational data.
- <mark style="background: #AD21D9;">Data Access Objects (DAO):</mark> Contains methods used for accessing database.

# <mark style="background: #FF5582A6;">SLIDE 12,13,14:</mark>

### <mark style="background: #AD21D9;">Entities:</mark>

Sets of related fields are defined as entities.

For each entity, <mark style="background: #AD21D9;">table</mark> is created within database object to hold items.

By default, ROOM creates a <mark style="background: #AD21D9;">column</mark> for each field defined in entity.

To store a field, ROOM must have <mark style="background: #AD21D9;">access</mark> to it.

2 options make field <mark style="background: #AD21D9;">public</mark>, or you can provide a getter and setter.

# <mark style="background: #FF5582A6;">SLIDE 16:</mark>

<mark style="background: #AD21D9;">Entities can have:</mark>
- An <mark style="background: #AD21D9;">empty</mark> constructor
- Constructor whose parameters contain types and names that <mark style="background: #AD21D9;">match</mark> those of fields in entity.
- <mark style="background: #AD21D9;">Partial</mark> constructors, such as a constructor that receives only some of the fields.

### <mark style="background: #AD21D9;">Primary Key:</mark>

Each entity must define at least 1 field as primary key.

Even when only 1 field, must still be annotated with ``@PrimaryKey``.

To assign <mark style="background: #AD21D9;">automatic</mark> IDs, set ``@PrimaryKey's autoGenerate`` property.

If entity has <mark style="background: #AD21D9;">composite</mark> primary key, use the ``primaryKeys`` property of the ``@Entity`` annotation.

### <mark style="background: #AD21D9;">Names:</mark>

<mark style="background: #AD21D9;">By default</mark>, ROOM uses class name as database table name.

For different name, set ``tableName`` property of ``@Entity``

<mark style="background: #AD21D9;">Caution:</mark> table names in SQLite are <mark style="background: #AD21D9;">case-insensitive</mark>.

ROOM uses field names as <mark style="background: #AD21D9;">column</mark> names in database.

Again, for a different name, add ``@ColumnInfo`` annotation to field.

### <mark style="background: #AD21D9;">Example:</mark>

```Kotlin
@Entity
data class User(
	@PrimaryKey val uid: Int,
	@ColumnInfo(name = "first_name") val firstName: String?,
	@ColumnInfo(name = "last_name") val lastName: String?
)
```

### <mark style="background: #AD21D9;">@NonNull:</mark>

``@NonNull`` denotes parameter, field, or method return value can never be null

Use for mandatory fields

Primary key <mark style="background: #AD21D9;">must</mark> use ``@NonNull``

### <mark style="background: #AD21D9;">Data Access Objects:</mark>

To <mark style="background: #AD21D9;">access</mark> app's data we work with data access objects, or DAOs.

The set of DAO forms main component of Room, as each DAO includes methods that offer <mark style="background: #AD21D9;">abstract</mark> access to your app's database.

Why use DAO class instead of query builders or direct queries?
1. <mark style="background: #AD21D9;">Separate</mark> different components of your database architecture.
2. Easily <mark style="background: #AD21D9;">mock</mark> database access to test app.

A DAO can be either an <mark style="background: #AD21D9;">interface</mark> or <mark style="background: #AD21D9;">abstract</mark> class.

If abstract class, can optionally have constructor that takes a ``RoomDatabase`` as only parameter.

Room creates each DAO implementation at <mark style="background: #AD21D9;">compile</mark> time.

<mark style="background: #AD21D9;">Note:</mark> Room doesn't support database access on Main Thread unless ``allowMainThreadQueries()`` called on builder.

### <mark style="background: #AD21D9;">Insert:</mark>

When you create a DAO method and annotate it with ``@Insert``

Room generates an implementation that inserts all parameters into the database in a single transaction.

```Kotlin
@Dao
interface MyDao {
	@Insert
	fun insertUser(user: User)
	@Insert
	fun insertBothUsers(user1: User, user2: User)
}
```

### <mark style="background: #AD21D9;">Update:</mark>

Update method modifies a set of entities, given as parameters

It uses a query that matches against primary key of each entity.

```Kotlin
@Dao
interface MyDao {
	@Update
	fun updateUsers(vararg users: User);
}
```

### <mark style="background: #AD21D9;">Delete:</mark>

Delete convenience method removes a set of entities, given as parameters, from database.

It uses the primary keys to find the entities to delete.

```Kotlin
@Dao
interface MyDao {
	@Delete
	fun deleteUsers(vararg users: User);
}
```

### <mark style="background: #AD21D9;">Queries:</mark>

``@Query`` is main annotation used in DAO classes.

It allows you to perform read/write operations on database.

Each @Query method is verified at compile time i.e. if there is problem with query, ``compilation error`` occurs instead of ``runtime failure``.

Below is a query that loads all users.

At compile time, Room knows it is querying all columns in user table.

If query contains syntax error or user table doesn't exist

Room displays error with appropriate message as app compiles.

```Kotlin
@Dao

interface MyDao {
	@Query("SELECT * FROM user")
	fun getAll(): List<User>
}
```

Passing parameters into queries performs filtering operations e.g. as displaying only users who are older than a certain age.

```Kotlin
@Dao
interface MyDao {
	@Query("SELECT * FROM user WHERE age > :minAge")
	fun loadAllUsersOlderThan(minAge)
}
```

You can also pass multiple parameters in a query.

```Kotlin
@Dao
interface MyDao {
	@Query("SELECT * FROM user WHERE age BETWEEN :minAge AND :maxAge")
	fun loadAllUsersBetweenAges(minAge, maxAge)
}
```

### <mark style="background: #AD21D9;">More Examples:</mark>

```Kotlin
@Query("DELETE FROM word_table")
fun deleteAll()

@Query("SELECT * from word_table ORDER BY word ASC")
fun getAllWords()

@Query("SELECT * FROM word_table WHERE word LIKE :word ")
fun findWord(String word)
```

### <mark style="background: #AD21D9;">Database:</mark>

<mark style="background: #AD21D9;">The class annotated with @Database should:</mark>
1. Be <mark style="background: #AD21D9;">abstract</mark> class that extends ``RoomDatabase``.
2. Include list of <mark style="background: #AD21D9;">entities</mark> associated with database within annotation.
3. Contain abstract method with 0 arguments and return class annotated with ``@Dao``.

```Kotlin
@Database(entities = [Word::class], version = 1)
abstract class WordRoomDatabase : RoomDatabase () {
	abstract fun wordDao : WordDao
```

At <mark style="background: #AD21D9;">runtime</mark>, an instance of Database is obtained by calling: ``Room.databaseBuilder()`` with class and database name

```Kotlin
val INSTANCE = Room.databaseBuilder(context,
	WordRoomDatabase::class.java, "word_database"
	).build();
```

### <mark style="background: #AD21D9;">Summary:</mark>

Room works with DAO and Entities

Entities define the database schema

DAO provides methods to access database

# <mark style="background: #FF5582A6;">SLIDE 35:</mark>