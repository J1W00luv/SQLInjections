
# SQL Injections Investigation

## **Aim:**
	To learn about SQL Injections, how they operate and can be used to modify SQL queries used in databases. Also find methods how they could be prevented.

## **Method:**
	1. Set up a safe environment: Use Kali VM and a vulnerable website created for learning purposes.
	2. SQL Injection: Use SQL to change the query content using user input.
	3. Analyse the output: Understand ways of detection & protection from SQL Injections.

## **Testing results:**
	
### First Website:
| Username | Password | Log in Successful? |
| -------- | -------- | ------------------ |
| admin’ OR ‘1’ = ‘1 | password123 | Y |

	Modified Query: SELECT * FROM users WHERE username = ‘admin’ OR ‘1’ =1’1 AND password = ‘password123’

### Second Website (CTF):
| Username | Password | Log in Successful? |
| -------- | -------- | ------------------ |
| admin' -- | password123 | Y |

	Modified Query: SELECT * FROM users WHERE username = ‘admin’ -- AND password = ‘password123’


## **Conclusion:**
	Both websites were vulnerable and did not have any user input checks, so it was easy to implement the needed SQL statement to make it always return True and log me in. To protect websites from similar SQL Injections developers could do multiple things, for example add input validation or placeholders, to stop the user input being executed in a query and added to the database instead.
