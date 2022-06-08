# login-api-with-email-validation

![image](https://user-images.githubusercontent.com/101902014/172558340-bc69b8b9-f860-4342-9440-4c5fa43ee50a.png)

#### sql code to create the the AppUser Database:
```sql
create table app_user (
       id BIGSERIAL not null,
        app_user_role varchar(255),
        email varchar(255),
        enabled boolean,
        first_name varchar(255),
        last_name varchar(255),
        locked boolean,
        password varchar(255),
        primary key (id)
    );
```

#### sql code to create the the ConfirmationToken Database:
```sql
    create table confirmation_token (
       id BIGSERIAL not null,
        confirmed_at timestamp,
        created_at timestamp not null,
        expires_at timestamp not null,
        token varchar(255) not null,
        app_user_id int8 not null,
        primary key (id)
    );
```
#### sql code to add the forign-key constraint:
```sql
	alter table confirmation_token 
       add constraint token_constraint 
       foreign key (app_user_id) 
       references app_user;
 ```
