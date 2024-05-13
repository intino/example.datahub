
# Intino Datahub Example

DataHub is a software platform that facilitates the creation, management, and distribution of events in event-driven systems. Using a domain-specific language (DSL), DataHub allows users to tailor their architecture to meet specific business needs, enhancing the integration and operability of real-time data systems.

## Starter code
The parameters

The main code (Main) of DataHub is responsible for initializing and configuring the platform. Here is the code:

    public static void main(String[] args) {
        DataHubConfiguration configuration = new DataHubConfiguration(args);
        NessGraph graph = GraphLoader.load();
        loadUsers(configuration.home(), graph);
        Box box = new DataHubBox(args).put(graph.core$());
        setLevel(Level.ERROR);
        box.start();
        Runtime.getRuntime().addShutdownHook(new Thread(box::stop));
    }

This code performs the following actions:
 - Initial Configuration: An instance of DataHubConfiguration is created using the arguments provided to the program. This must be provided in the format "name"="value". The arguments are:
   - home (required): Specifies the directory where DataHub will store its files.
   - broker_port (required): Specifies the port for the JMS OpenWire protocol.
   - broker_secondary_port (required): Specifies the port for the MQTT protocol.
   - backup_directory (optional): The directory where periodic backups of the datalake changes can be made.
   - SSL Encryption args (optional): Additional parameters related to SSL encryption for the protocols can be provided. Concretely: "keystore_path", "keystore_password", "truststore_path" and "truststore_password".
 - Graph Loading: A graph (NessGraph) is loaded using the graph loader.
 - User Loading: Users are loaded from the location specified in the configuration.
 - Box Initialization: An instance of DataHubBox is created with the provided arguments, and the core of the graph is added to the box.
 - Logging Level Configuration: The logging level is set to ERROR.
 - Box Start: The box is started.
 - Shutdown Management: A shutdown hook is added to stop the box properly when the program finishes.



## Features
The platform includes a set of features that make it useful for various applications:

 - Management of a messaging broker supporting JMS OpenWire and MQTT protocols.  
 - Datalake for storing and organizing events.
 - Configurable terminals for client interaction.
 - Shared datamarts for customized data projections.
 - These features make DataHub a practical tool for businesses looking to optimize their data flows and improve decision-making based on events.

## Contribution
We welcome any contributions to improve DataHub! If you wish to contribute, please follow the steps in our contribution document.

## License
DataHub is licensed under the MIT License.

Follow the link for more information:
https://intino.systems/wiki/index.php?title=Datahub