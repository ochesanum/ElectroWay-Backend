
# ElectroWay API
## ElectroWay Backend Team1

Electroway is an application designed to make charging your electric car and planning a route as easy and intuitive as possible.
Team 1, consisting of Harabagiu Radu, Ochesanu Mihnea, Curca Andrei, Rotariu Cosmin si Isac Iulian was responsible for everything in the API excepting routing, database design, error handling and a few endpoints. As a note, while we did develop most endpoints, team 3 helped standardize the code by refactoring a number of the first endpoints we'd developed, mainly by making liberal use of Lombok.

The functionalities to which Radu Harabagiu contributed are:

1. The JWT-based authentication filter, containing
	* An entry point
	* The filter itself, implemented by extending OncePerRequestFilter
	* An utility class for working with the JWTtoken

1. A role-based system, which only allows some roles(containing some privileges) access to some endpoints
	* The roles and their privileges are added to the database when the application is ran, if they do not already exist
	* An admin user with the admin role is created at the same time, while any other user attempting to give themselves the admin role will not be able to do so

1. Implemented the Springboot Security component, by extending the WebSecurityConfiguererAdapter, providing
	* DRY implementation for password salting and JWT parsing(with the help of the filter mentioned previously)
	* Cross-Site Request Forgery (CSRF) defense through a csrf token(disabled to better showcase testing in postman)
	* Cross-Origin Resource Sharing (CORS), which allowed the Web Interface developed by the Web team to interact with the API from their web address, while restricting the access of others to potentially sensitive resources

1. A peer to peer payment component utilizing PayPal's API, which allows drivers to pay station owner directly, without an intermediary

Endpoints: User,Login,PayPal,PayPalDetail

The functionalities to which Mihnea Ochesanu contributed are:

1. An Email-based password reset as well as account confirmation upon registration

1. Field validation, built utilizing Passay (a Java-based password generation and validation library), containing
    * A PasswordValidator created from a rule set
    * A Password Constraint Validator utilizing list of several rules to help validate passwords by passay

1. Swagger Documentation for an easier understanding of our endpoints

Endpoints: Station, ChargingPoint, ChargingPlug,

The application has been deployed using heroku, using the papertrail addon to have access to the java output
