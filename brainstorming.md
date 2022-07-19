Brainstorming 

Users: 

	User_id
	host_id
	Name
	Email
	Password
	
Recipes: 
	Recipe_id
	Recipe_name
	Instructions
	Privacy
	Date

Ingredients: 
	Ingredient_id 
	Ingredient_name

Grocery List: 
	grocery _list _id
	Grocery-list
	Date
Occasion: 
	Occasion_id
	Occasion_name
	Occasion_date
	Occasion_location


Table Ideas

Users: 
	User_id
	Occassion_id
	Name 
	Email
	Password
	Bio
	Date_joined

Recipes: 
	Recipe_id
	User_id
	occasion_id
	Recipe_name
	Instructions
	Privacy
	Date

Ingredients: 
	Ingredient_id
	Recipe_id
	Grocery-list-id
	Ingredient_name
Grocery-list: 
	Grocery_list_id
	recipe_id
	User-id
	occasion _id
	text
Occasions: 
	Occasion_id
	Host_id
	Occasion_date
	Occasion_location
	Occassion_name
	
Hosts: 
	Host-id
	user_id
	Host-name
	
Followers: 
	Follow-id 
	Follower_id
	Followed_id

	


Relationships: 
	One to many: 
		User to recipes, one user can have many recipes
		Recipe to ingredients, one recipe can have many ingredients	
		Grocery list to ingredients, one grocery list can have many ingredients
		Occasion to recipes, one occasion can have many recipes
		Occasion to users, one occasion can have many people going
		Host to occasions, one host can have multiple occasions 
		
		
		
	Many to many:
Followers, many followers can follow many people  
	One to One: 
		Recipe to grocery list , a recipe will only have one grocery list
		User to host, a host will be only one user
		Occasion to grocery list, an organized occasion should only have one grocery list 
		
	
Columns : 

Users: 
	User id: identify the user, 
	User, name, password, email - login info and basic user info, 
	Occasion id: identify what users are going to an occasion

Recipes: 

	Recipe id : identify recipe
	User id: what user made the recipe
	Recipe name/instructions: recipe info, 
	Private: whether people can see it or not
	Grocery list id: what grocery list contains the ingredients for this recipe
	Occasion id: if this recipe belongs to any occasions

Ingredients: 
	Ingredient name: info 
	Ingredient id: identify
	Grocery list id: what grocery list this item belongs to 

Grocery list : 
	Id: identify 
	Name: name of list 
	Recipe id: what recipe this list belongs to 
	Occasion id: what occasion this list belongs to 
	List: ingredients in the list 

Occasions: 
	Name: what its called
	Location: where it is 
	Date : when it is 
	Host id: whose hosting 
	Occasion id: identify

Hosts: 
	Id: identify
	User id: which user is the host
	Host name: name of host 

Followers: 
	Follow id: identify 	
	Follower id: id of follower 
	Followed id: id of followed user 

SQL code: 

CREATE TABLE "users" (
  "user_id" SERIAL PRIMARY KEY,
  "name" VARCHAR(50) NOT NULL,
  "email" VARCHAR(65) NOT NULL,
  "password" VARCHAR(100) NOT NULL,
  "bio" VARCHAR(300) NOT NULL,
  "joined_date" DATE NOT NULL,
  "occassion_id" INTEGER
);
 
CREATE TABLE "recipes" (
  "recipe_id" SERIAL PRIMARY KEY,
  "user_id" INTEGER NOT NULL,
  "recipe_name" VARCHAR(30),
  "instructions" VARCHAR(1500),
  "private" BOOLEAN NOT NULL,
  "grocery_list_id" INTEGER NOT NULL,
  "occassion_id" INTEGER NOT NULL
);
 
CREATE TABLE "occasions" (
  "occassion_id" SERIAL PRIMARY KEY,
  "host_id" INTEGER NOT NULL,
  "occasion_date" DATE NOT NULL,
  "occasion_location" VARCHAR(75) NOT NULL,
  "occasion_name" VARCHAR(75) NOT NULL
);
 
CREATE TABLE "grocery_list" (
  "grocery_list_id" SERIAL PRIMARY KEY,
  "recipe_id" INTEGER NOT NULL,
  "user_id" INTEGER NOT NULL,
  "occassion_id" INTEGER NOT NULL,
  "groceries" VARCHAR(500) NOT NULL
);
 
CREATE TABLE "ingredients" (
  "ingedient_id" SERIAL PRIMARY KEY,
  "recipe_id" INTEGER NOT NULL,
  "grocery_list_id" INTEGER NOT NULL,
  "ingredient_name" VARCHAR(30) NOT NULL
);
 
CREATE TABLE "hosts" (
  "host_id" SERIAL PRIMARY KEY,
  "user_id" INTEGER,
  "host_name" VARCHAR(50)
);
 
CREATE TABLE "followers" (
  "follow_id" SERIAL PRIMARY KEY,
  "follower_id" INTEGER NOT NULL,
  "followed_id" INTEGER NOT NULL
);

