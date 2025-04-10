# Postman-test-real-web-api


Project test API on the one of real web app what rely on api endpoint and use Angular as main frontend framework. 
It checks how CRUD operations work behind the scene when user can use interface to do actions but invisible for eye
operation are executed and I pointed out these operations, delivered required data, checked outputs allow to delivery
proper data to fronted templated to corrent programming views managing data.
 
Basically I used only variables from collection and local as main keeper to ease this configuration. 
There is easy way to replace them or extend to use also environments, global in exported json file with postman tests.

Main variable what has to be define and it is in colleciton is URL api to test:
	"https://conduit-api.bondaracademy.com/api"

The approach I used allow user to use this project without any changes. Each test is set in hierarchy and each step 
delivery needed data and variables to collection variables and use them later to proceed and finish tests defined in requests.

Explanation of name test and endpoints:
1 postNewAcc:
	creates new uniq email and login and also constant password and save in collection variables
	use collection variables and create new user in api request post
	after create user fetch token and save in colleciton var
	include basic tests status, timeout, code
	
2 postLogin:
	shoot to endpoint api to log in via development environment which was added manually 
	receive token and save token to collection variables to reuse it in tests
	include basic tests status, timeout, code
	
Both login and NewAcc create token and save to env. Login save token in env of collection and this will be use in requests.

3 postArticle: 
	create new artice from environments of collection created in pre request script.
	
4 getArticlesCreated:
	fetch aritcle created in previous request. Check that status, code, title, body, slug, tag, desciption and username is correctly added
5 getArticles:
	fetch all aritcles then from list select first article which should be the one created in previous request. 
	Check that status, code, title, body, slug, tag, desciption and username is correctly added
6 updateArticle:
	get article created in test by slug in url then chance desc and body, check changed fields
7 getArticlesAfterUpdate:
	get list all articles and check that last one is updated correctly
8 DeleteArticle:
	delete article created in tests. 
9 getArtcilesAfterDelete:
	get list of all articles, then check that first of them doesnt contain title and slug from our main article.

How to check path to pasted file of json (to use in postman)? 	
pwd for linux and cd for windows. You have to be in the right folder in terminal. 
	
What you need as requirements to start that project and execute test?
1 basic option to use it manually:
	Install postman and download file crudRestCollection.postman_collection.json from git
	git clone ...... 
	it saves folder on your system. Then click import in postman colleciton saved and use runner collection 
	or test after test execute them manually.
2 extended verion with newman and use it via terminal
	it requires node.js, installation of newman.
3 extended 2.0 with newman and jenkins.
	it requires node.js, installation of newman and jenkins.

	


Runner collection can be set and parametrize for example  iterations, data, delay, cookies, variables, environments.
Monitor: 
	schedule time of execute tests	
	select proper team members to send reports from tests
	
    // pm.environment.set("variable_key", "variable_value");
    // pm.environment.set("jwt_token", pm.response.json().access_token)
    // var jsonData = JSON.parse(responseBody);
    // pm.environment.set("jwt_token", jsonData.access_token);