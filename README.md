# Backend-API-Documentation
​​## EV Management System

TECH PIONEERS TEAM:
IBRAHIM NIMER
JAFAR RAMADN
MOYAD HAMDAN
ABDULRAHMAN RADWAN
YASSIN AL FARAWAN
YAZAN HUSSIEN

Project Overview: 

A brief description of the app and its purpose: 

 Developing a backend system for an Electric Vehicle (EV) Charging Station and Service Management application using ASP.NET. This system will provide users with the ability to manage their electric vehicles, book charging stations, track vehicle usage, and schedule maintenance. The application will also include services such as booking emergency repairs or purchasing spare parts, and it will feature user authentication, role-based access control, and a dynamic admin dashboard for system management. 

The tech stack used: 

Backend Framework: ASP.NET Core  

Database: SQL Server (with Entity Framework for ORM)  

Authentication: ASP.NET Identity with JWT Tokens  

API Design: RESTful API design with well-defined endpoints  

Key features and functionality of the API: 

1. Account Management  

User Authentication & Authorization: 

Provides login and registration functionalities. 

Handles password management and account verification. 

Account Details Management: 

Fetches and updates account-related information such as personal details. 

Allows clients to deactivate or delete their accounts. 

Role Management: 

Manages roles and permissions within the system. 

Supports assigning roles such as admin, client, owner, and servicer. 

 

2. Admin Management  

User & Role Management: 

Provides comprehensive functionality for managing user accounts. 

Allows assigning roles, revoking access, and managing role-based permissions. 

 

System Monitoring: 

Offers admin tools to monitor system health and view system logs. 

Payment & Transaction Auditing: 

Allows for reviewing and managing payment transactions across the platform. 

Post and Comment Moderation: 

Enables admin to manage posts and comments, ensuring compliance with platform policies. 

Session & Notification Management: 

Manages user sessions and broadcasts important notifications to users. 

 

3. Client Management  

Session Management: 

Clients can start, end, and manage their charging or service sessions. 

Payment Transactions: 

Enables clients to view payment history and manage transactions. 

Favorites Management: 

Allows clients to save and retrieve favorite charging stations and services. 

Vehicle & Booking Management: 

Clients can add, view, and manage their vehicles and service bookings. 

Service Request & Feedback: 

Enables clients to submit service requests and provide feedback on services received. 

 

 

Notifications: 

Clients receive important notifications regarding their sessions, bookings, or services. 

4.Owner Management  

Charging Station & Charger Management: 

Owners can create, update, and manage their charging stations and chargers. 

Provides access to charger details and allows for station updates or deletions. 

Maintenance Logs: 

Enables owners to track and manage maintenance logs for their stations. 

Post and Comment Management: 

Owners can manage posts and comments related to their stations or services. 

Session Management: 

Allows owners to view sessions conducted at their charging stations. 

Location Management: 

Owners can add or update locations related to their charging stations. 

 

5. Servicer Management 

Service Information & Requests: 

Provides the ability to create, view, update, and delete service information. 

Manages service requests, including status updates and service request history. 

Booking Management: 

Enables creation and management of service bookings. 

Allows for updating the status of bookings or canceling them as needed. 

Notification Handling: 

Servicers can create and manage notifications, ensuring clients are informed about their services. 

Post and Comment Management: 

Servicers have access to post and comment functionality for interaction with clients and owners. 

 

Conclusion 

The API provides a wide range of functionalities tailored to each type of user (Admin, Client, Owner, Servicer, and Account). The features include robust management tools for handling user sessions, services, payments, notifications, posts, and comments. Each interface offers a comprehensive set of methods to ensure seamless operations and interactions between clients, owners, servicers, and administrators within the system. 

 

 

 

 

 

 

 

 

 

API Endpoints: 

Account: 

1. Register 

HTTP Method: POST 

Route: /api/account/Register 

Parameters: 

Body: RegisterdAccountDto (JSON object) – Includes details for account registration such as username, password, and roles. 

Valid roles: Admin, Client, Owner, Servicer. 

Response: 

201 Created: Returns AccountRegisterdResponseDto (JSON object) with account details if registration is successful. 

400 Bad Request: If registration fails or invalid role is provided. 

500 Internal Server Error: If an unexpected error occurs. 

Shape 

2. Login 

HTTP Method: POST 

Route: /api/account/Login 

Parameters: 

Body: LoginDto (JSON object) – Includes UserName and Password for authentication. 

Response: 

200 OK: Returns AccountRegisterdResponseDto (JSON object) with account details if authentication is successful. 

401 Unauthorized: If invalid username or password is provided. 

500 Internal Server Error: If an unexpected error occurs. 

Shape 

3. LogOut 

HTTP Method: POST 

Route: /api/account/Logout 

Parameters: 

Query: username (string) – The username of the account to log out. 

Response: 

200 OK: Returns a success message if logout is successful. 

500 Internal Server Error: If an unexpected error occurs. 

Shape 

4. Profile 

HTTP Method: GET 

Route: /api/account/Profile 

Authorization: Requires authentication. 

Parameters: None. 

Response: 

200 OK: Returns AccountRegisterdResponseDto (JSON object) with profile details if the user is authenticated. 

401 Unauthorized: If the user is not authenticated or does not exist. 

500 Internal Server Error: If an unexpected error occurs. 

Shape 

5. DeleteAccount 

HTTP Method: DELETE 

Route: /api/account/DeleteAccount 

Authorization: Requires Admin role. 

Parameters: 

Query: username (string) – The username of the account to delete. 

Response: 

200 OK: Returns a success message and account details if the account is deleted successfully. 

404 Not Found: If the account with the specified username is not found. 

500 Internal Server Error: If an unexpected error occurs. 

Admin: 

1. Client Management 

1.1 Get All Clients 

HTTP Method: GET 

Route: /api/Admins/Clients 

Parameters: None 

Response: 

200 OK: Returns a list of all clients (ClientResponseDto[]). 

1.2 Get Client by ID 

HTTP Method: GET 

Route: /api/Admins/Clients/{id} 

Parameters: 

Path: id (int) – Client's ID. 

Response: 

200 OK: Returns details of the specified client (ClientResponseDto). 

404 Not Found: If no client is found with the specified ID. 

1.3 Delete Client 

HTTP Method: DELETE 

Route: /api/Admins/Clients/{id} 

Parameters: 

Path: id (int) – Client's ID. 

Response: 

204 No Content: Client successfully deleted. 

404 Not Found: If no client is found with the specified ID. 

Shape 

2. Provider Management 

2.1 Get All Providers 

HTTP Method: GET 

Route: /api/Admin/providers 

Parameters: None 

Response: 

200 OK: Returns a list of all providers (ProviderResponseDto[]). 

2.2 Get Provider by ID 

HTTP Method: GET 

Route: /api/Admin/providers/{id} 

Parameters: 

Path: id (int) – Provider's ID. 

Response: 

200 OK: Returns details of the specified provider (ProviderResponseDto). 

404 Not Found: If no provider is found with the specified ID. 

2.3 Delete Provider 

HTTP Method: DELETE 

Route: /api/Admin/providers/{id} 

Parameters: 

Path: id (int) – Provider's ID. 

Response: 

204 No Content: Provider successfully deleted. 

Shape 

3. Client Subscriptions Management 

3.1 Get Client Subscriptions 

HTTP Method: GET 

Route: /api/Admins/Clients/{clientId}/Subscriptions 

Parameters: 

Path: clientId (int) – Client's ID. 

Response: 

200 OK: Returns a list of subscriptions for the specified client. 

404 Not Found: If no subscriptions are found for the client. 

3.2 Remove Client Subscription 

HTTP Method: DELETE 

Route: /api/Admins/Subscriptions/{clientSubscriptionId} 

Parameters: 

Path: clientSubscriptionId (int) – Subscription ID. 

Response: 

204 No Content: Subscription successfully deleted. 

404 Not Found: If no subscription is found with the specified ID. 

Shape 

 

4. Subscription Plan Management 

4.1 Get All Subscription Plans 

HTTP Method: GET 

Route: /api/Admin/SubscriptionPlans 

Parameters: None 

Response: 

200 OK: Returns a list of all subscription plans (SubscriptionPlanResponseDto[]). 

4.2 Get Subscription Plan by ID 

HTTP Method: GET 

Route: /api/Admin/SubscriptionPlans/{id} 

Parameters: 

Path: id (int) – Subscription Plan ID. 

Response: 

200 OK: Returns details of the specified subscription plan. 

404 Not Found: If no subscription plan is found with the specified ID. 

4.3 Create Subscription Plan 

HTTP Method: POST 

Route: /api/Admin/SubscriptionPlans 

Parameters: 

Body: SubscriptionPlanDto – Contains details of the new subscription plan. 

Response: 

200 OK: Returns the created subscription plan (SubscriptionPlanDtoResponse). 

400 Bad Request: If invalid subscription plan data is provided. 

4.4 Delete Subscription Plan 

HTTP Method: DELETE 

Route: /api/Admin/SubscriptionPlans/{id} 

Parameters: 

Path: id (int) – Subscription Plan ID. 

Response: 

204 No Content: Subscription plan successfully deleted. 

404 Not Found: If no subscription plan is found with the specified ID. 

 

Notifications Management 

GET 

Route: api/Admin/Clients/{clientId}/Notifications 

Parameters: 

clientId: The ID of the client whose notifications are being retrieved. 

Response: List of notifications for the specified client. 

POST 

Route: api/Admin/Clients/{clientId}/Notifications 

Parameters: 

clientId: The ID of the client (must match the ClientId in the request body). 

notificationDto: Notification data to be added. 

Response: Created notification object. 

Shape 

Charging Station Management 

GET 

Route: api/Admin/ChargingStations 

Response: List of all charging stations. 

GET 

Route: api/Admin/ChargingStations/{id} 

Parameters: 

id: The ID of the charging station to retrieve. 

Response: Charging station details. 

DELETE 

Route: api/Admin/ChargingStations/{id} 

Parameters: 

id: The ID of the charging station to delete. 

Response: No content (204). 

Shape 

Vehicle Management 

GET 

Route: api/Admin/Vehicles 

Response: List of all vehicles. 

GET 

Route: api/Admin/Vehicles/{id} 

Parameters: 

id: The ID of the vehicle to retrieve. 

Response: Vehicle details. 

DELETE 

Route: api/Admin/Vehicles/{id} 

Parameters: 

id: The ID of the vehicle to delete. 

Response: No content (204). 

Shape 

Booking Management 

GET 

Route: api/Admin/Bookings 

Response: List of all bookings. 

GET 

Route: api/Admin/Bookings/{id} 

Parameters: 

id: The ID of the booking to retrieve. 

Response: Booking details. 

DELETE 

Route: api/Admin/Bookings/{id} 

Parameters: 

id: The ID of the booking to delete. 

Response: No content (204). 

Shape 

Location Management 

GET 

Route: api/Admin/Locations 

Response: List of all locations. 

GET 

Route: api/Admin/Locations/{id} 

Parameters: 

id: The ID of the location to retrieve. 

Response: Location details. 

POST 

Route: api/Admin/Locations 

Parameters: 

locationDto: Data for the new location. 

Response: Created location object. 

PUT 

Route: api/Admin/Locations/{id} 

Parameters: 

id: The ID of the location to update. 

locationDto: Updated location data. 

Response: No content (204). 

DELETE 

Route: api/Admin/Locations/{id} 

Parameters: 

id: The ID of the location to delete. 

Response: No content (204). 

 

Shape 

Post Management 

GET 

Route: api/Admin/Posts 

Response: List of all posts, including each post's details and associated comments. 

GET 

Route: api/Admin/Posts/{id} 

Parameters: 

id: The ID of the post to retrieve. 

Response: Details of the specified post, including comments. 

POST 

Route: api/Admin/Posts 

Parameters: 

postDto: Data for the new post. 

Response: Created post object with its ID. 

PUT 

Route: api/Admin/Posts/{id} 

Parameters: 

id: The ID of the post to update. 

postDto: Updated post data. 

Response: Updated post details. 

DELETE 

Route: api/Admin/Posts/{id} 

Parameters: 

id: The ID of the post to delete. 

Response: No content (204). 

Shape 

Comment Management 

GET 

Route: api/Admin/Comments 

Response: List of all comments, including each comment's details. 

GET 

Route: api/Admin/Comments/{id} 

Parameters: 

id: The ID of the comment to retrieve. 

Response: Details of the specified comment. 

POST 

Route: api/Admin/Comments 

Parameters: 

commentDto: Data for the new comment. 

Response: Created comment object. 

PUT 

Route: api/Admin/Comments/{id} 

Parameters: 

id: The ID of the comment to update. 

commentDto: Updated comment data. 

Response: Updated comment details. 

DELETE 

Route: api/Admin/Comments/{id} 

Parameters: 

id: The ID of the comment to delete. 

Response: No content (204). 

 

Client: 

Session Management 

Get All Sessions 

Route: GET /sessions 

Parameters: clientId 

Returns: List of sessions for the client. 

Get Session by ID 

Route: GET /sessions/{sessionId} 

Parameters: sessionId 

Returns: Session details. 

Start a Session 

Route: POST /sessions 

Body: SessionDto 

Returns: Started session details. 

End a Session 

Route: PUT /sessions/{sessionId} 

Parameters: sessionId 

Returns: No content (204). 

Payment Transactions Management 

Get Client Payments 

Route: GET /PaymentTransaction/{sessionId} 

Parameters: sessionId 

Returns: List of payments for the session. 

Add Payment 

Route: POST /PaymentTransaction 

Body: PaymentTransactionDto 

Returns: Added payment details. 

Remove Payment 

Route: DELETE /PaymentTransaction/{paymentId} 

Parameters: paymentId 

Returns: No content (204). 

Favorites Management 

Get Charging Station Favorites 

Route: GET /ChargingStationsFavorites/{clientId} 

Parameters: clientId 

Returns: List of charging station favorites for the client. 

Get Service Info Favorites 

Route: GET /ServiceInfosFavorites/{clientId} 

Parameters: clientId 

Returns: List of service info favorites for the client. 

Add Charging Station Favorite 

Route: POST /ChargingStationFavorites 

Body: FavoriteChargingStationDto 

Returns: Added charging station favorite. 

Add Service Info Favorite 

Route: POST /ServiceInfoFavorites 

Body: FavoriteServiceInfoDto 

Returns: Added service info favorite. 

Remove Charging Station Favorite 

Route: DELETE /ChargingStationFavorites/{favoriteId} 

Parameters: favoriteId 

Returns: No content (204). 

Remove Service Info Favorite 

Route: DELETE /ServiceInfoFavorites/{favoriteId} 

Parameters: favoriteId 

Returns: No content (204). 

Vehicle Management 

Get Client Vehicles 

Route: GET /vehicles/{clientId} 

Parameters: clientId 

Returns: List of vehicles for the client. 

Get Vehicle by ID 

Route: GET /vehicle/{vehicleId} 

Parameters: vehicleId 

Returns: Vehicle details. 

Add Vehicle 

Route: POST /vehicle 

Body: VehicleDto 

Returns: Added vehicle details. 

Remove Vehicle 

Route: DELETE /vehicles/{vehicleId} 

Parameters: vehicleId 

Returns: No content (204). 

Booking Management 

Get Client Bookings 

Route: GET /bookings/{clientId} 

Parameters: clientId 

Returns: List of bookings for the client. 

Get Booking by ID 

Route: GET /booking/{bookingId} 

Parameters: bookingId 

Returns: Booking details. 

Add Booking 

Route: POST /bookings 

Body: BookingDto 

Returns: Added booking details. 

Remove Booking 

Route: DELETE /bookings/{bookingId} 

Parameters: bookingId 

Returns: No content (204). 

Service Request Management 

Get Client Service Requests 

Route: GET /service-requests/{clientId} 

Parameters: clientId 

Returns: List of service requests for the client. 

Get Service Request by ID 

Route: GET /service-request/{requestId} 

Parameters: requestId 

Returns: Service request details. 

Create Service Request 

Route: POST /service-requests 

Body: ClientServiceRequestDto 

Returns: Created service request details. 

Delete Service Request 

Route: DELETE /service-requests/{requestId} 

Parameters: requestId 

Returns: No content (204). 

Feedback Management 

Get Client Feedbacks 

Route: GET /feedbacks/{clientId} 

Parameters: clientId 

Returns: List of feedbacks for the client. 

Add Feedback 

Route: POST /feedbacks 

Body: FeedbackDto 

Returns: Added feedback details. 

Remove Feedback 

Route: DELETE /feedbacks/{feedbackId} 

Parameters: feedbackId 

Returns: No content (204). 

Notification Management 

Get Client Notifications 

Route: GET /notifications/{clientId} 

Parameters: clientId 

Returns: List of notifications for the client. 

Get Notification by ID 

Route: GET /notification/{notificationId} 

Parameters: notificationId 

Returns: Notification details. 

Post Management 

Get All Posts 

Route: GET /posts 

Returns: List of all posts. 

Add Post 

Route: POST /posts 

Body: PostDto 

Returns: Added post details. 

Update Post by ID 

Route: PUT /Posts/{id} 

Parameters: id 

Body: PostDto 

Returns: Updated post details. 

Delete Post 

Route: DELETE /posts/{postId} 

Parameters: postId 

Returns: No content (204). 

Comment Management 

Get All Comments 

Route: GET /comments 

Returns: List of all comments. 

Add Comment 

Route: POST /comments 

Body: CommentDto 

Returns: Added comment details. 

Update Comment by ID 

Route: PUT /Comments/{id} 

Parameters: id 

Body: CommentDto 

Returns: Updated comment details. 

Delete Comment 

Route: DELETE /comments/{commentId} 

Parameters: commentId 

Returns: No content (204). 

Owner: 

Charging Station Management 

Get All Charging Stations 

HTTP Method: GET 

Route Pattern: chargingstations 

Parameters: None 

Response: IEnumerable<ChargingStationResponseDto> - List of all charging stations. 

Get Charging Station by ID 

HTTP Method: GET 

Route Pattern: chargingstations/{id} 

Parameters: id (int) - ID of the charging station. 

Response: ChargingStationResponseDto - Details of the specified charging station. 

Create Charging Station 

HTTP Method: POST 

Route Pattern: chargingstations 

Parameters: stationDtoRequest (ChargingStationDto) - Data for the new charging station. 

Response: CreatedAtAction - Location of the newly created charging station. 

Update Charging Station 

HTTP Method: PUT 

Route Pattern: chargingstations/{id} 

Parameters: id (int) - ID of the charging station; stationDtoRequest (ChargingStationDto) - Updated data. 

Response: No Content. 

Delete Charging Station 

HTTP Method: DELETE 

Route Pattern: chargingstations/{id} 

Parameters: id (int) - ID of the charging station. 

Response: No Content. 

Get Chargers by Station ID 

HTTP Method: GET 

Route Pattern: stations/{stationId}/chargers 

Parameters: stationId (int) - ID of the charging station. 

Response: IEnumerable<ChargerResponseDto> - List of chargers for the specified station. 

Get Charger by ID 

HTTP Method: GET 

Route Pattern: chargers/{id} 

Parameters: id (int) - ID of the charger. 

Response: ChargerResponseDto - Details of the specified charger. 

Create Charger 

HTTP Method: POST 

Route Pattern: chargers 

Parameters: chargerDtoRequest (ChargerDto) - Data for the new charger. 

Response: ChargerResponseDto - Details of the created charger. 

Update Charger 

HTTP Method: PUT 

Route Pattern: chargers/{id} 

Parameters: id (int) - ID of the charger; chargerDtoRequest (ChargerDto) - Updated data. 

Response: No Content. 

Delete Charger 

HTTP Method: DELETE 

Route Pattern: chargers/{id} 

Parameters: id (int) - ID of the charger. 

Response: No Content. 

Maintenance Log Management 

Get Maintenance Logs by Station ID 

HTTP Method: GET 

Route Pattern: maintenance/{stationId} 

Parameters: stationId (int) - ID of the charging station. 

Response: IEnumerable<MaintenanceLogDtoResponse> - List of maintenance logs. 

Add Maintenance Log 

HTTP Method: POST 

Route Pattern: maintenance 

Parameters: logDtoRequest (MaintenanceLogDto) - Data for the new log. 

Response: MaintenanceLogDtoResponse - Details of the created maintenance log. 

Remove Maintenance Log 

HTTP Method: DELETE 

Route Pattern: maintenance/{id} 

Parameters: id (int) - ID of the maintenance log. 

Response: No Content. 

Notification Management 

Create Notification 

HTTP Method: POST 

Route Pattern: OwnerNotifications 

Parameters: notificationDto (NotificationDto) - Data for the new notification. 

Response: NotificationResponseDto - Details of the created notification. 

Get Notification by ID 

HTTP Method: GET 

Route Pattern: OwnerNotifications/{notificationId} 

Parameters: notificationId (int) - ID of the notification. 

Response: NotificationResponseDto - Details of the specified notification. 

Get Notifications by Client ID 

HTTP Method: GET 

Route Pattern: OwnerNotifications/client/{clientId} 

Parameters: clientId (int) - ID of the client. 

Response: IEnumerable<NotificationResponseDto> - List of notifications for the specified client. 

Location Management 

Get All Locations 

HTTP Method: GET 

Route Pattern: locations 

Parameters: None 

Response: IEnumerable<LocationResponseDto> - List of all locations. 

Get Location by ID 

HTTP Method: GET 

Route Pattern: locations/{id} 

Parameters: id (int) - ID of the location. 

Response: LocationResponseDto - Details of the specified location. 

Create Location 

HTTP Method: POST 

Route Pattern: locations 

Parameters: locationDtoRequest (LocationDto) - Data for the new location. 

Response: LocationResponseDto - Details of the created location. 

Update Location 

HTTP Method: PUT 

Route Pattern: locations/{id} 

Parameters: id (int) - ID of the location; locationDtoRequest (LocationDto) - Updated data. 

Response: No Content. 

Delete Location 

HTTP Method: DELETE 

Route Pattern: locations/{id} 

Parameters: id (int) - ID of the location. 

Response: No Content. 

Post Management 

Get All Posts 

HTTP Method: GET 

Route Pattern: posts 

Parameters: None 

Response: IEnumerable<PostResponseDto> - List of all posts. 

Add Post 

HTTP Method: POST 

Route Pattern: posts 

Parameters: postDto (PostDto) - Data for the new post. 

Response: PostResponseDto - Details of the created post. 

Update Post by ID 

HTTP Method: PUT 

Route Pattern: Posts/{id} 

Parameters: id (int) - ID of the post; postDto (PostDto) - Updated data. 

Response: PostResponseDto - Updated post details. 

Delete Post 

HTTP Method: DELETE 

Route Pattern: posts/{postId} 

Parameters: postId (int) - ID of the post. 

Response: No Content. 

Comment Management 

Get All Comments 

HTTP Method: GET 

Route Pattern: comments 

Parameters: None 

Response: IEnumerable<CommentResponseDto> - List of all comments. 

Add Comment 

HTTP Method: POST 

Route Pattern: comments 

Parameters: commentDto (CommentDto) - Data for the new comment. 

Response: CommentResponseDto - Details of the created comment. 

Update Comment by ID 

HTTP Method: PUT 

Route Pattern: Comments/{id} 

Parameters: id (int) - ID of the comment; commentDto (CommentDto) - Updated data. 

Response: CommentResponseDto - Updated comment details. 

Delete Comment 

HTTP Method: DELETE 

Route Pattern: comments/{commentId} 

Parameters: commentId (int) - ID of the comment. 

Response: No Content. 

Booking Management 

Get Bookings by Charging Station 

HTTP Method: GET 

Route Pattern: station/{stationId} 

Parameters: stationId (int) - ID of the charging station. 

Response: IEnumerable<BookingDto> - List of bookings for the specified station. 

Get Booking by ID 

HTTP Method: GET 

Route Pattern: {bookingId} 

Parameters: bookingId (int) - ID of the booking. 

Response: BookingDto - Details of the specified booking. 

Get Bookings by Date Range 

HTTP Method: GET 

Route Pattern: station/{stationId}/range 

Parameters: stationId (int); startDate (DateTime); endDate (DateTime). 

Response: IEnumerable<BookingDto> - List of bookings within the specified date range. 

Get Pending Bookings 

HTTP Method: GET 

Route Pattern: station/{stationId}/pending 

Parameters: stationId (int) - ID of the charging station. 

Response: IEnumerable<BookingDto> - List of pending bookings. 

Create Booking 

HTTP Method: POST 

Route Pattern: bookings 

Parameters: bookingDtoRequest (BookingDto) - Data for the new booking. 

Response: BookingDto - Details of the created booking. 

Cancel Booking 

HTTP Method: DELETE 

Route Pattern: bookings/{bookingId} 

Parameters: bookingId (int) - ID of the booking. 

Response: No Content. 

 

Servicer: 

Service Info Management 

Create Service Info 

HTTP Method: POST 

Route Pattern: serviceinfo 

Parameters: serviceInfoDto (ServiceInfoRequestDto) - Data for the new service info. 

Response: CreatedAtAction - Location of the newly created service info. 

Get Service Info by ID 

HTTP Method: GET 

Route Pattern: serviceinfo/{id} 

Parameters: id (int) - ID of the service info. 

Response: ServiceInfoResponseDto - Details of the specified service info. 

Get All Service Infos 

HTTP Method: GET 

Route Pattern: serviceinfos 

Parameters: None 

Response: IEnumerable<ServiceInfoResponseDto> - List of all service infos. 

Update Service Info 

HTTP Method: PUT 

Route Pattern: serviceinfo/{id} 

Parameters: id (int) - ID of the service info; serviceInfoDto (ServiceInfoRequestDto) - Updated data. 

Response: No Content. 

Delete Service Info 

HTTP Method: DELETE 

Route Pattern: serviceinfo/{id} 

Parameters: id (int) - ID of the service info. 

Response: No Content. 

Service Request Management 

Get Service Request by ID 

HTTP Method: GET 

Route Pattern: servicerequest/{id} 

Parameters: id (int) - ID of the service request. 

Response: ServiceRequestResponseDto - Details of the specified service request. 

Get Service Requests by Service Info ID 

HTTP Method: GET 

Route Pattern: servicerequests/serviceinfo/{serviceInfoId} 

Parameters: serviceInfoId (int) - ID of the service info. 

Response: IEnumerable<ServiceRequestResponseDto> - List of service requests for the specified service info. 

Update Service Request Status 

HTTP Method: PUT 

Route Pattern: servicerequest/{id}/status 

Parameters: id (int) - ID of the service request; status (string) - New status for the request. 

Response: No Content. 

Delete Service Request 

HTTP Method: DELETE 

Route Pattern: servicerequest/{id} 

Parameters: id (int) - ID of the service request. 

Response: No Content. 

Notification Management 

Create Notification 

HTTP Method: POST 

Route Pattern: ServicerNotifications 

Parameters: notificationDto (NotificationDto) - Data for the new notification. 

Response: CreatedAtRoute - Location of the newly created notification. 

Get Notification by ID 

HTTP Method: GET 

Route Pattern: ServicerNotifications/{notificationId} 

Parameters: notificationId (int) - ID of the notification. 

Response: NotificationResponseDto - Details of the specified notification. 

Get Notifications by Client ID 

HTTP Method: GET 

Route Pattern: ServicerNotifications/client/{clientId} 

Parameters: clientId (int) - ID of the client. 

Response: IEnumerable<NotificationResponseDto> - List of notifications for the specified client. 

Post Management 

Get All Posts 

HTTP Method: GET 

Route Pattern: posts 

Parameters: None 

Response: IEnumerable<PostResponseDto> - List of all posts. 

Add Post 

HTTP Method: POST 

Route Pattern: posts 

Parameters: postDto (PostDto) - Data for the new post. 

Response: CreatedAtAction - Location of the newly created post. 

Update Post by ID 

HTTP Method: PUT 

Route Pattern: Posts/{id} 

Parameters: id (int) - ID of the post; postDto (PostDto) - Updated data. 

Response: PostResponseDto - Updated post details. 

Delete Post 

HTTP Method: DELETE 

Route Pattern: posts/{postId} 

Parameters: postId (int) - ID of the post. 

Response: No Content. 

Comment Management 

Get All Comments 

HTTP Method: GET 

Route Pattern: comments 

Parameters: None 

Response: IEnumerable<CommentResponseDto> - List of all comments. 

Add Comment 

HTTP Method: POST 

Route Pattern: comments 

Parameters: commentDto (CommentDto) - Data for the new comment. 

Response: CommentResponseDto - Details of the created comment. 

Update Comment by ID 

HTTP Method: PUT 

Route Pattern: Comments/{id} 

Parameters: id (int) - ID of the comment; commentDto (CommentDto) - Updated data. 

Response: CommentResponseDto - Updated comment details. 

Delete Comment 

HTTP Method: DELETE 

Route Pattern: comments/{commentId} 

Parameters: commentId (int) - ID of the comment. 

Response: No Content.
 
 

Data Models & ERD: 

Description : 

Admin 
Represents an administrator with an associated account, responsible for managing the application and overseeing user activities. 

 

Client 
Represents a client user with an associated account, who can book services, provide feedback, and manage their subscriptions. 

 

Provider 
Represents a service provider with an associated account, responsible for delivering services and managing service requests. 

 

Booking 
Represents a reservation made by a client for a charging station, linking the client, vehicle, and charging station. 

 

Charger 
Represents a charging device associated with a charging station, facilitating the charging of electric vehicles. 

 

ChargingStation 
Represents a location with multiple chargers where clients can charge their vehicles, linked to specific providers and locations. 

 

Comment 
Represents user feedback on posts, associated with both the commenting account and the post being commented on. 

 

ChargingStationFavorite 
Represents a client’s favorite charging station, allowing easy access to preferred charging locations. 

 

 

ServiceInfoFavorite 
Represents a client’s favorite service information, helping clients quickly access preferred services. 

 

Feedback 
Represents feedback provided by clients regarding services, associated with both the client and the service info. 

 

Location 
Represents a geographic location where charging stations are situated, providing context for their placement. 

 

MaintenanceLog 
Represents logs for maintenance activities performed on charging stations, helping track service history. 

 

Notification 
Represents alerts or messages sent to clients regarding updates or changes, enhancing communication. 

 

PaymentTransaction 
Represents a financial transaction made by a client, linked to a specific session and client. 

 

Post 
Represents content created by users, which can receive comments and feedback. 

 

ServiceInfo 
Represents details about services offered by providers, which clients can request and provide feedback on. 

 

ServiceRequest 
Represents a request made by a client for a specific service, linking clients to service providers. 

 

Session 
Represents a user session for clients, tracking interactions and activities related to charging stations. 

 

SubscriptionPlan 
Represents various subscription options available to clients, defining terms and benefits. 

 

ClientSubscription 
Represents the relationship between clients and their chosen subscription plans, facilitating access to services. 

 

Vehicle 
Represents vehicles owned by clients, which can be associated with bookings and service requests. 

ERD: 
4. Git Workflow: 
GitHub Link :  https://github.com/LTUCProject/MidProject 

 

