# Practice assignments belonging to the 'Bicep: What's new?' session / workshop

Before you start:
- Run ``az bicep upgrade`` to ensure you have the latest version

1. Create a Bicep file ``keyvault.bicep`` that deploys a key vault and a single secret into that key vault. 
   - The file should take a parameter for the key vaults name
   - The name of the secret should be ``service-bus-name``
   - The value for the secret can be anything you like
2. Now create a new file, ``keyvault.bicepparam`` that references this template and provide a value for the parameter
3. Experiment with leaving out parameters, providing values for non existin paramters in Visual Studio Code

4. Create a second bicep file ``servicebusnamespace.bicep`` that deploys a service bus namespace
   - The file should take a parameter for the service bus' name

5. Create a new file ``servicebusnamespace.bicepparam`` that provides a value for this parameter
   - Get the secret from the Key Vault using the ``az.getSecret(..)`` function

6. Update the file ``servicebusnamespace.bicep``
   - Define  a new type ``QueueConfiguration`` with at least three properties on the queue configuration. Use properties from queue resource type you can find at https://learn.microsoft.com/en-us/azure/templates/microsoft.servicebus/namespaces/queues?pivots=deployment-language-bicep
   - Add two parameters of type ``QueueConfiguration`` with the names ``moviesConfiguration`` and ``authorsConfiguration``
   - Define a second and third resource, both of type queue with the names ``movies`` and ``authors``. Use the ``moviesConfiguration`` and ``authorsConfiguration`` parameters to configure the queues

7. Open the ``servicebusnamespace.bicepparameters`` and configure the parameters to remove any compilation errors

8. Make a change to any of your files to generate a warning.

9. Remove the warning by adding a ``#disable-next-line`` directive

10. Make another change that introduces a warning

11. Create a bicepconfig.json to suppress all warnings of that type

12. Update your bicepconfig.json to enable the experimental feature for resource typed parameters and outputs

13. Create a new file ``orchestrator.bicep`` that deploys your existing two bicep files.
  - Update the  ``keyvault.bicep`` file to export the secret resource
  - Update the ``servicebusnamespace.bicep`` file to take a keyvault secret resource as a parameter
  - Update the ``servicebusnamespace.bicep`` file to use the secret value as the servicebusnamespace name

14. In Azure, create a new resource group and create a container registry in that resource group

15. Deploy the ``keyvault.bicep`` file as a bicep module to the registry

16. Update the ``orechestrator.bicep`` file to use the Key Vault module from the registry
  - For bonus points: experiment with versions
  - For bonus points: use Google and MS Learn to implement ``moduleAliases``

17. Enable the experimental feature for exporting and importing types.

18. Move the definition of ``QueueConfiguration`` to a new file ``QueueConfiguration.bicep``

19. Import the ``QueueConfiguration`` into the ``servicebusnamespace.bicep`` file

20. Deploy the ``keyvault.bicep`` file as a template spec

21. Deploy the ``keyvault.bicep`` template spec using the Azure CLI (not demo'd)

22. Deploy the ``keyvault.bicep`` template spec using another Bicep file

23. Fiddle around with deployment stacks
   - Create a template with a few resources and deploy as a deployment stack into Azure
   - Remove and add a few resources and redeploy. View resource changes and deployment stack state in the Azure portal
   - Experiment with deleting resources instead of detaching them.

24. If you have made it all the way here, very well done and go grab some coffee!