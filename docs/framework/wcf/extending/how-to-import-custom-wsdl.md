---
title: "HOW TO：匯入自訂 WSDL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af43baabfe979baa5c6fd7010c8be4dc72a3be9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-import-custom-wsdl"></a>HOW TO：匯入自訂 WSDL
這個主題會描述如何匯入自訂 WSDL。 若要處理自訂 WSDL，您必須實作 <xref:System.ServiceModel.Description.IWsdlImportExtension> 介面。  
  
### <a name="to-import-custom-wsdl"></a>匯入自訂 WSDL  
  
1.  實作 <xref:System.ServiceModel.Description.IWsdlImportExtension>。 實作 <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> 方法，以便於匯入中繼資料前進行修改。 實作 <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> 和 <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> 方法，以便修改從中繼資料匯入的合約和端點。 若要存取匯入的合約或端點，請使用相對應的內容物件 (<xref:System.ServiceModel.Description.WsdlContractConversionContext> 或 <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>)：  
  
    ```  
    public class WsdlDocumentationImporter : IWsdlImportExtension  
       {  
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
       }  
    ```  
  
2.  設定用戶端應用程式以使用自訂 WSDL 匯入工具。 請注意，如果正在使用 Svcutil.exe，您應該針對 Svcutil.exe (Svcutil.exe.config) 將此組態新增至組態檔：  
  
    ```xml  
    <system.serviceModel>  
          <client>  
            <endpoint   
              address="http://localhost:8000/Fibonacci"   
              binding="wsHttpBinding"  
              contract="IFibonacci"  
            />  
            <metadata>  
              <wsdlImporters>  
                <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
              </wsdlImporters>  
            </metadata>  
          </client>  
        </system.serviceModel>  
    ```  
  
3.  建立新的 <xref:System.ServiceModel.Description.WsdlImporter> 執行個體 (在包含您要匯入之 WSDL 文件的 <xref:System.ServiceModel.Description.MetadataSet> 執行個體中傳遞)，並且呼叫 <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>：  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);          System.Collections.ObjectModel.Collection<ContractDescription> contracts  = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a>請參閱  
 [中繼資料](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [匯出和匯入中繼資料](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)  
 [自訂 WSDL 發行集](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)
