# POI-SMA-API PREVIEW
 
POI-SMA-API is an API rest  that facilitates show the potontiel functiolaties of the system POI-SMA-API using a Multi-Agent System (MAS) approach, specifically designed for Point of Interest (POI) recommendations. This application leverages the power of MAS to provide intelligent and personalized recommendations to users based on their preferences and behavior.

![MAS-ARCHITECTURE](https://github.com/Yacine300/POI-SMA-API/blob/main/MAS.png))

## ![2699](https://github.com/user-attachments/assets/cc1d6d85-22eb-49f7-adbc-195259b96bbb)Features

- **POI Recommendations**: Utilize the API to generate recommendations for points of interest based on user preferences, location, and historical data.
- **Multi-Agent System**: Harness the capabilities of a MAS architecture to enable collaborative and distributed recommendation generation.
- **Test Version**: Please note that this is a test version of the API, intended for experimentation and evaluation purposes. It may not have all features fully implemented or optimized for production use.
 
## ![1f4ca](https://github.com/user-attachments/assets/3636cac1-263b-4ad2-9598-78656df49455)![1f4c8](https://github.com/user-attachments/assets/e4d57b0a-34b3-4075-933d-f5452f9f46a7) Evaluation
The system has been tested with 15 real users. Each user passed through 3 phases:

- Cold start and recommending POIs.
- After defining certain activities such as clicks, likes, and comments.
- By considering friends.
  
---> Please check the `evaluation-test.text` file for detailed evaluation results.

### Technologies Used

![Node.js Icon](https://img.icons8.com/color/100/nodejs.png) ![Express Icon](https://img.icons8.com/ios/100/express-js.png) ![MongoDB Icon](https://img.icons8.com/color/100/mongodb.png)


## Documentation

NOT AVAIBLE FOR THE MOMENT.

#![1f916](https://github.com/user-attachments/assets/96ba8937-5f82-4b62-b6f2-685d57f80242) Multi-Agent System Overview

The system operates with seven specialized agents, each playing a crucial role in enhancing performance and providing accurate recommendations. Here’s a detailed overview of each agent and their specific functions:


 ## ![31_20e3](https://github.com/user-attachments/assets/4c54af71-c120-4f64-8f77-2264b1ccd627). Builder Agent
- **Role**: Acts as the front-end component, developed using Flutter. It is responsible for real-time interaction with the user.
- **Responsibilities**:
  - **Real-Time Monitoring**: Listens to and monitors user activities such as clicks, likes, comments, ratings, and friend relations.
  - **State Management Integration**: Utilizes state management within the app to capture and manage user interactions effectively.
  - **Data Collection**: Aggregates user activities and stores them temporarily.
  - **Data Transmission**: Sends aggregated data to the AsynchAgent only when a sufficient amount of new activities is collected to ensure the recommendation process is efficient and effective.

## ![32_20e3](https://github.com/user-attachments/assets/2fbdbcb4-2691-4d10-8a48-6833cf6a683f). AsynchAgent

- **Role**: Functions as the asynchronous data handler and storage agent.
- **Responsibilities**:
  - **Data Storage**: Securely stores user activity data received from the Builder Agent into a database. This allows for future use and historical reference.
  - **Data Forwarding**: Forwards the stored data to the Matching Agent for further processing and recommendation generation.
  - **Error Handling**: Ensures data integrity by preserving the last activities history. In case of any issues or exceptions, the system can rely on this historical data, preventing data loss and maintaining system reliability.

## ![33_20e3](https://github.com/user-attachments/assets/fd95b1ab-d971-4120-bf4d-7911c06d0ade). Matching Agent

- **Role**: Serves as the master coordinator for recommendation generation.
- **Responsibilities**:
  - **Data Distribution**: Distributes data to the slave agents (CollabAgent, ImplicitTrustAgent, ExplicitTrustAgent, and ContentBasedAgent) for processing.
  - **Recommendation Calculation**: Uses the Broda calculation method to combine the recommendation results from the slave agents into a comprehensive and balanced final recommendation.
  - **Database Update**: Updates the final recommendation results in the database to reflect the latest data.
  - **Real-Time Updates**: Ensures that the Flutter app receives updated recommendation scores via WebSocket in real-time, providing users with immediate feedback.
  - **Cycle Management**: Manages the recommendation process in predefined cycles. After each cycle, the recommendation style for points of interest remains stable until new data is processed.

## ![34_20e3](https://github.com/user-attachments/assets/559106bf-c744-4d51-a487-dd0781cf5878). CollabAgent
- **Role**: Handles collaborative filtering methods.
- **Responsibilities**:
  - **Collaborative Filtering**: Calculates recommendation scores based on the preferences and behaviors of users with similar ratings . It leverages user interaction data to identify patterns and suggest relevant points of interest.

## ![35_20e3](https://github.com/user-attachments/assets/7182d448-44ec-4da7-8a2d-0b2c75e298f7). ImplicitTrustAgent

- **Role**: Specializes in implicit trust metrics.
- **Responsibilities**:
  - **Implicit Trust Calculation**: Computes recommendation scores based on implicit trust metrics, which are inferred from user interactions. This includes signals such as frequent visits, engagement time, and indirect endorsements.
  - **Real Friend Data**: Utilizes the list of real friends provided by the user and stored in the database to generate recommendations. This approach ensures that trust metrics are grounded in actual relationships.

## ![36_20e3](https://github.com/user-attachments/assets/f4667816-e765-4efa-88af-8d5fc0aa0e0e). ExplicitTrustAgent

- **Role**: Focuses on explicit trust metrics.
- **Responsibilities**:
  - **Explicit Trust Calculation**: Determines recommendation scores using explicit trust metrics, such as click , likes , comments and endorsements provided by users.
  - **Friend Prediction**: Employs advanced techniques to guess potential friends of the user based on rating patterns and preferences, even if these individuals are not explicitly listed as friends.

## ![37_20e3](https://github.com/user-attachments/assets/932dd176-67b6-4b05-bdcb-482998c28c5b). ContentBasedAgent

- **Role**: Utilizes content-based filtering methods.
- **Responsibilities**:
  - **Content-Based Filtering**: Generates recommendation scores by analyzing the attributes of pois that users have shown interest in. It recommends similar pois based on these attributes, focusing on matching content characteristics.
    

## System Architecture and Communication

- ![1f512](https://github.com/user-attachments/assets/f7d4b92c-4218-4c04-8de4-de8ddfefcc98)**Agent Environments**: Each agent operates in its own dedicated environment or runtime. This separation ensures optimal performance and efficient resource usage for each agent's specific tasks.
- ![1f50c](https://github.com/user-attachments/assets/65b764a2-0c52-491c-bbd1-8ce4fb54ee07)**Communication**: Agents communicate via WebSocket, which facilitates real-time data exchange and updates. This enables the system to operate cohesively and respond promptly to changes and interactions.
- ![1fa9b](https://github.com/user-attachments/assets/34164367-f558-46fd-a056-32cf5aa21ae3)**Fault Tolerance**: The system is designed to continue functioning even if one agent encounters problems or issues. This resilience ensures uninterrupted operation and maintains the overall integrity of the recommendation process.

This detailed architecture ensures a robust and efficient recommendation system, leveraging specialized agents to provide accurate and timely recommendations based on user interactions and preferences.


## Contributing

No contributions are allowed for the moment.

## License

This project is licensed ,  please check the LICENCE.md file.

## Acknowledgements

Special thanks to [Sebihi Yacine Sami El Hak] for his work, support, and inspiration for this project.

---

[WANDER WISE]
