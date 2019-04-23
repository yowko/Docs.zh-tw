---
title: HOW TO：撰寫 ServiceContractGenerator 的延伸模組
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: c9e10efccf0d51e6b78aace1296d227a78a9f91d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340616"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="62dfd-102">HOW TO：撰寫 ServiceContractGenerator 的延伸模組</span><span class="sxs-lookup"><span data-stu-id="62dfd-102">How to: Write an Extension for the ServiceContractGenerator</span></span>
<span data-ttu-id="62dfd-103">本主題說明如何撰寫 <xref:System.ServiceModel.Description.ServiceContractGenerator> 的擴充。</span><span class="sxs-lookup"><span data-stu-id="62dfd-103">This topic describes how to write an extension for the <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span></span> <span data-ttu-id="62dfd-104">您可以在作業行為上實作 <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> 介面，或在合約行為上實作 <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> 介面來達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="62dfd-104">This can be done by implementing the <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interface on an operation behavior or implementing the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span> <span data-ttu-id="62dfd-105">本主題說明如何在合約行為上實作 <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> 介面。</span><span class="sxs-lookup"><span data-stu-id="62dfd-105">This topic shows how to implement the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span>  
  
 <span data-ttu-id="62dfd-106"><xref:System.ServiceModel.Description.ServiceContractGenerator> 會從 <xref:System.ServiceModel.Description.ServiceEndpoint>、<xref:System.ServiceModel.Description.ContractDescription> 和 <xref:System.ServiceModel.Channels.Binding> 執行個體中產生服務合約、用戶端類型，與用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="62dfd-106">The <xref:System.ServiceModel.Description.ServiceContractGenerator> generates service contracts, client types, and client configurations from <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances.</span></span> <span data-ttu-id="62dfd-107">一般來說，您可以從服務中繼資料匯入 <xref:System.ServiceModel.Description.ServiceEndpoint>、<xref:System.ServiceModel.Description.ContractDescription>，和 <xref:System.ServiceModel.Channels.Binding> 執行個體，然後使用這些執行個體來產生程式碼以呼叫服務。</span><span class="sxs-lookup"><span data-stu-id="62dfd-107">Typically, you import <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances from service metadata and then use these instances to generate code to call the service.</span></span> <span data-ttu-id="62dfd-108">此範例會使用 <xref:System.ServiceModel.Description.IWsdlImportExtension> 實作來處理 WSDL 附註，然後將程式碼產生擴充加入至匯入的合約中，以便在產生的程式碼中產生註解。</span><span class="sxs-lookup"><span data-stu-id="62dfd-108">In this example, an <xref:System.ServiceModel.Description.IWsdlImportExtension> implementation is used to process WSDL annotations and then add code generation extensions to the imported contracts to generate comments on the generated code.</span></span>  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="62dfd-109">若要撰寫 ServiceContractGenerator 的擴充</span><span class="sxs-lookup"><span data-stu-id="62dfd-109">To write an extension for the ServiceContractGenerator</span></span>  
  
1. <span data-ttu-id="62dfd-110">實作 <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>。</span><span class="sxs-lookup"><span data-stu-id="62dfd-110">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="62dfd-111">若要修改產生的服務合約，請使用已傳入至 <xref:System.ServiceModel.Description.ServiceContractGenerationContext> 方法的 <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="62dfd-111">To modify the generated service contract, use the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instance passed into the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> method.</span></span>  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. <span data-ttu-id="62dfd-112">在相同類別上實作 <xref:System.ServiceModel.Description.IWsdlImportExtension>。</span><span class="sxs-lookup"><span data-stu-id="62dfd-112">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension> on the same class.</span></span> <span data-ttu-id="62dfd-113"><xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> 方法可以處理特定的 WSDL 擴充 (在此情況下為 WSDL 附註)，方法是將程式碼產生擴充加入至下列匯入的 <xref:System.ServiceModel.Description.ContractDescription> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="62dfd-113">The <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method can process a specific WSDL extension (WSDL annotations in this case) by adding a code generation extension to the imported <xref:System.ServiceModel.Description.ContractDescription> instance.</span></span>  
  
    ```  
    public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)  
       {  
                // Contract documentation  
             if (context.WsdlPortType.Documentation != null)  
             {  
                    context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));  
             }  
             // Operation documentation  
             foreach (Operation operation in context.WsdlPortType.Operations)  
             {  
                if (operation.Documentation != null)  
                {  
                   OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);  
                   if (operationDescription != null)  
                   {  
                            operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));  
                   }  
                }  
             }  
          }  
          public void BeforeImport(ServiceDescriptionCollection wsdlDocuments, XmlSchemaSet xmlSchemas, ICollection<XmlElement> policy)   
            {  
                Console.WriteLine("BeforeImport called.");  
            }  
  
          public void ImportEndpoint(WsdlImporter importer, WsdlEndpointConversionContext context)   
            {  
                Console.WriteLine("ImportEndpoint called.");  
            }  
    ```  
  
3. <span data-ttu-id="62dfd-114">將 WSDL 匯入工具加入至您的用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="62dfd-114">Add the WSDL importer to your client configuration.</span></span>  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. <span data-ttu-id="62dfd-115">在用戶端程式碼中，建立 `MetadataExchangeClient` 並呼叫 `GetMetadata`。</span><span class="sxs-lookup"><span data-stu-id="62dfd-115">In the client code, create a `MetadataExchangeClient` and call `GetMetadata`.</span></span>  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. <span data-ttu-id="62dfd-116">建立 `WsdlImporter` 並呼叫 `ImportAllContracts`。</span><span class="sxs-lookup"><span data-stu-id="62dfd-116">Create a `WsdlImporter` and call `ImportAllContracts`.</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. <span data-ttu-id="62dfd-117">為每個合約建立 `ServiceContractGenerator` 並呼叫 `GenerateServiceContractType`。</span><span class="sxs-lookup"><span data-stu-id="62dfd-117">Create a `ServiceContractGenerator` and call `GenerateServiceContractType` for each contract.</span></span>  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <span data-ttu-id="62dfd-118">在實作 <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> 的特定合約上，會針對每個合約行為自動呼叫 <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>。</span><span class="sxs-lookup"><span data-stu-id="62dfd-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> is called automatically for each contract behavior on a given contract that implements <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="62dfd-119">這個方法會接著修改傳入的 <xref:System.ServiceModel.Description.ServiceContractGenerationContext>。</span><span class="sxs-lookup"><span data-stu-id="62dfd-119">This method can then modify the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passed in.</span></span> <span data-ttu-id="62dfd-120">在這個範例中會加入註解。</span><span class="sxs-lookup"><span data-stu-id="62dfd-120">In this example comments are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62dfd-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62dfd-121">See also</span></span>

- [<span data-ttu-id="62dfd-122">中繼資料</span><span class="sxs-lookup"><span data-stu-id="62dfd-122">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="62dfd-123">如何：匯入自訂 WSDL</span><span class="sxs-lookup"><span data-stu-id="62dfd-123">How to: Import Custom WSDL</span></span>](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
