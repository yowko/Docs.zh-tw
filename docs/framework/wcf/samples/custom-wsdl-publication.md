---
title: 自訂 WSDL 發行物
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: 725b62a26d640e242010a01ff810ea90d5cc53bc
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418431"
---
# <a name="custom-wsdl-publication"></a>自訂 WSDL 發行物
這個範例會示範如何：  
  
-   實作自訂 <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> 屬性 (Attribute) 上的 <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>，以便將屬性 (Attribute) 的屬性 (Property) 匯出為 WSDL 附註。  
  
-   實作 <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> 以匯入自訂 WSDL 附註。  
  
-   在自訂合約行為和自訂作業行為上分別實作 <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> 和 <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType>，將匯入的附註寫入為 CodeDOM 中的註解，以用於匯入的合約和作業。  
  
-   使用<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType>來下載 WSDL、<xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>匯入使用自訂的 WSDL 匯入工具，和<xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType>產生 Windows Communication Foundation (WCF) 用戶端程式碼具有 WSDL 附註做 / / 和 '' C# 和 Visual 中的註解基本的。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
## <a name="service"></a>服務  
 在這個範例中，會使用兩個自訂屬性來標示服務。 第一個是 `WsdlDocumentationAttribute`，它會在建構函式中接受字串，您可以套用此屬性來為合約介面或作業提供描述其使用方式的字串。 第二個是 `WsdlParamOrReturnDocumentationAttribute`，您可以將它套用至傳回值或參數，在作業中描述這些值。 下列範例示範使用這些屬性所描述的服務合約 `ICalculator`。  
  
```  
// Define a service contract.      
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
// Document it.  
[WsdlDocumentation("The ICalculator contract performs basic calculation services.")]  
public interface ICalculator  
{  
    [OperationContract]  
    [WsdlDocumentation("The Add operation adds two numbers and returns the result.")]  
    [return:WsdlParamOrReturnDocumentation("The result of adding the two arguments together.")]  
    double Add(  
      [WsdlParamOrReturnDocumentation("The first value to add.")]double n1,   
      [WsdlParamOrReturnDocumentation("The second value to add.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Subtract operation subtracts the second argument from the first.")]  
    [return:WsdlParamOrReturnDocumentation("The result of the second argument subtracted from the first.")]  
    double Subtract(  
      [WsdlParamOrReturnDocumentation("The value from which the second is subtracted.")]double n1,   
      [WsdlParamOrReturnDocumentation("The value that is subtracted from the first.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Multiply operation multiplies two values.")]  
    [return:WsdlParamOrReturnDocumentation("The result of multiplying the first and second arguments.")]  
    double Multiply(  
      [WsdlParamOrReturnDocumentation("The first value to multiply.")]double n1,   
      [WsdlParamOrReturnDocumentation("The second value to multiply.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Divide operation returns the value of the first argument divided by the second argument.")]  
    [return:WsdlParamOrReturnDocumentation("The result of dividing the first argument by the second.")]  
    double Divide(  
      [WsdlParamOrReturnDocumentation("The numerator.")]double n1,   
      [WsdlParamOrReturnDocumentation("The denominator.")]double n2  
    );  
}  
```  
  
 `WsdlDocumentationAttribute` 會實作 <xref:System.ServiceModel.Description.IContractBehavior> 和 <xref:System.ServiceModel.Description.IOperationBehavior>，以便在開啟服務時將屬性執行個體新增至對應的 <xref:System.ServiceModel.Description.ContractDescription> 或 <xref:System.ServiceModel.Description.OperationDescription>。 這個屬性還會實作 <xref:System.ServiceModel.Description.IWsdlExportExtension>。 呼叫 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> 時，會傳入用來匯出中繼資料的 <xref:System.ServiceModel.Description.WsdlExporter> 和含有服務描述物件的 <xref:System.ServiceModel.Description.WsdlContractConversionContext> 做為參數，以啟用匯出之中繼資料的修改作業。  
  
 在這個範例中，會依據匯出的內容物件是否含有 <xref:System.ServiceModel.Description.ContractDescription> 或 <xref:System.ServiceModel.Description.OperationDescription> 而定，從使用文字屬性 (Property) 的屬性 (Attribute) 擷取註解，並將它新增至 WSDL 附註項目，如下列程式碼所示。  
  
```  
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
    if (contractDescription != null)  
    {  
        // Inside this block it is the contract-level comment attribute.  
        // This.Text returns the string for the contract attribute.  
        // Set the doc element; if this isn't done first, there is no XmlElement in the   
        // DocumentElement property.  
        context.WsdlPortType.Documentation = string.Empty;  
        // Contract comments.  
        XmlDocument owner = context.WsdlPortType.DocumentationElement.OwnerDocument;  
        XmlElement summaryElement = owner.CreateElement("summary");  
        summaryElement.InnerText = this.Text;  
        context.WsdlPortType.DocumentationElement.AppendChild(summaryElement);  
    }  
    else  
    {  
        Operation operation = context.GetOperation(operationDescription);  
        if (operation != null)  
        {  
            // We are dealing strictly with the operation here.  
            // This.Text returns the string for the operation-level attributes.  
            // Set the doc element; if this isn't done first, there is no XmlElement in the   
            // DocumentElement property.  
            operation.Documentation = String.Empty;  
  
            // Operation C# triple comments.  
            XmlDocument owner = operation.DocumentationElement.OwnerDocument;  
            XmlElement newSummaryElement = owner.CreateElement("summary");  
            newSummaryElement.InnerText = this.Text;  
            operation.DocumentationElement.AppendChild(newSummaryElement);  
```  
  
 如果是要匯出某項作業，這個範例會使用反映 (Reflection) 來為參數和傳回值取得任何 `WsdlParamOrReturnDocumentationAttribute` 值，並將它們新增至該作業的 WSDL 附註項目，如下所示。  
  
```  
// Get returns information  
ParameterInfo returnValue = operationDescription.SyncMethod.ReturnParameter;  
object[] returnAttrs = returnValue.GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
if (returnAttrs.Length != 0)  
{  
    // <returns>text.</returns>  
    XmlElement returnsElement = owner.CreateElement("returns");  
    returnsElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)returnAttrs[0]).ParamComment;  
    operation.DocumentationElement.AppendChild(returnsElement);  
}  
  
// Get parameter information.  
ParameterInfo[] args = operationDescription.SyncMethod.GetParameters();  
for (int i = 0; i < args.Length; i++)  
{  
    object[] docAttrs = args[i].GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
    if (docAttrs.Length == 1)  
    {  
        // <param name="Int1">Text.</param>  
        XmlElement newParamElement = owner.CreateElement("param");  
        XmlAttribute paramName = owner.CreateAttribute("name");  
        paramName.Value = args[i].Name;  
        newParamElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)docAttrs[0]).ParamComment;  
        newParamElement.Attributes.Append(paramName);  
        operation.DocumentationElement.AppendChild(newParamElement);  
    }  
}  
```  
  
 這個範例會接著使用下列組態檔，以標準方式發行中繼資料。  
  
```xml  
<services>  
  <service   
      name="Microsoft.ServiceModel.Samples.CalculatorService"  
      behaviorConfiguration="CalculatorServiceBehavior">  
    <!-- ICalculator is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    <!-- the mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
    <endpoint address="mex"  
              binding="mexHttpBinding"  
              contract="IMetadataExchange" />  
  </service>  
</services>  
  
<!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="svcutil-client"></a>Svcutil 用戶端  
 這個範例不使用 Svcutil.exe。 這個範例會在 generatedClient.cs 檔案中提供合約，以便在示範自訂 WSDL 匯入作業與程式碼產生作業之後叫用服務。 若要在這個範例中使用下列自訂 WSDL 匯入工具，您可以執行 Svcutil.exe，並指定 `/svcutilConfig` 選項，來提供此範例 (其參考 `WsdlDocumentation.dll` 程式庫) 中所使用之用戶端組態檔的路徑。 不過，若要載入 `WsdlDocumentationImporter`，Svuctil.exe 就必須能夠找到並載入 `WsdlDocumentation.dll` 程式庫，這表示應先在全域組件快取中、路徑中或是在包含 Svcutil.exe 的同一個目錄中註冊此程式庫。 對於像這樣的基本範例，最簡單的方式就是將 Svcutil.exe 和用戶端組態檔複製到 `WsdlDocumentation.dll` 所在的相同目錄中，再從那裡加以執行。  
  
## <a name="the-custom-wsdl-importer"></a>自訂 WSDL 匯入工具  
 自訂的 <xref:System.ServiceModel.Description.IWsdlImportExtension> 物件 `WsdlDocumentationImporter` 也會實作 <xref:System.ServiceModel.Description.IContractBehavior> 和 <xref:System.ServiceModel.Description.IOperationBehavior> (要新增至匯入的 ServiceEndpoints)，以及 <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> 和 <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> (會在建立合約或作業程式碼時被叫用來修改程式碼產生)。  
  
 在 <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> 方法中，這個範例首先會判斷 WSDL 附註是在合約層級還是在作業層級，然後在適當的範圍內將本身新增為行為，並傳遞匯入的附註文字至其建構函式。  
  
```  
public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)  
{  
    // Contract Documentation  
    if (context.WsdlPortType.Documentation != null)  
    {  
        // System examines the contract behaviors to see whether any implement IWsdlImportExtension.  
        context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));  
    }  
    // Operation Documentation  
    foreach (Operation operation in context.WsdlPortType.Operations)  
    {  
        if (operation.Documentation != null)  
        {  
            OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);  
            if (operationDescription != null)  
            {  
                // System examines the operation behaviors to see whether any implement IWsdlImportExtension.  
                operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));  
            }  
        }  
    }  
}  
```  
  
 接下來，系統會在產生程式碼時叫用 <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> 和 <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> 方法，並傳遞適當的內容資訊。 這個範例會格式化自訂 WSDL 附註，再將它們當做註解插入 CodeDom 中。  
  
```  
public void GenerateContract(ServiceContractGenerationContext context)  
{  
    Debug.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(FormatComments(text));  
}  
  
public void GenerateOperation(OperationContractGenerationContext context)  
{  
    context.SyncMethod.Comments.AddRange(FormatComments(text));  
    Debug.WriteLine("In generate operation.");  
}  
```  
  
## <a name="the-client-application"></a>用戶端應用程式  
 用戶端應用程式會在應用程式組態檔中指定自訂 WSDL 匯入工具來加以載入。  
  
```xml  
<client>  
  <endpoint address="http://localhost/servicemodelsamples/service.svc"   
  binding="wsHttpBinding"   
  contract="ICalculator" />  
  <metadata>  
    <wsdlImporters>  
      <extension type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
    </wsdlImporters>  
  </metadata>  
</client>  
```  
  
 一旦已指定自訂匯入工具，WCF 中繼資料系統會將自訂匯入工具載入至任何<xref:System.ServiceModel.Description.WsdlImporter>為此目的建立。 這個範例會使用 <xref:System.ServiceModel.Description.MetadataExchangeClient> 來下載中繼資料、使用已正確設定的 <xref:System.ServiceModel.Description.WsdlImporter> 以使用範例所建立之自訂匯入工具來匯入中繼資料，以及使用 <xref:System.ServiceModel.Description.ServiceContractGenerator> 將修改的合約資訊編譯成 Visual Basic 和 C# 用戶端程式碼，此程式碼可以用於 Visual Studio 以支援 Intellisense，也可以編譯為 XML 文件。  
  
```  
/// From WSDL Documentation:  
///   
/// <summary>The ICalculator contract performs basic calculation   
/// services.</summary>   
///   
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.ServiceModel.Samples", ConfigurationName="ICalculator")]  
public interface ICalculator  
{  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Add operation adds two numbers and returns the   
    /// result.</summary><returns>The result of adding the two arguments   
    /// together.</returns><param name="n1">The first value to add.</param><param   
    /// name="n2">The second value to add.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Add", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/AddResponse")]  
    double Add(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Subtract operation subtracts the second argument from the   
    /// first.</summary><returns>The result of the second argument subtracted from the   
    /// first.</returns><param name="n1">The value from which the second is   
    /// subtracted.</param><param name="n2">The value that is subtracted from the   
    /// first.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Subtract", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/SubtractResponse")]  
    double Subtract(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Multiply operation multiplies two values.</summary><returns>The   
    /// result of multiplying the first and second arguments.</returns><param   
    /// name="n1">The first value to multiply.</param><param name="n2">The second value   
    /// to multiply.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Multiply", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/MultiplyResponse")]  
    double Multiply(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Divide operation returns the value of the first argument divided   
    /// by the second argument.</summary><returns>The result of dividing the first   
    /// argument by the second.</returns><param name="n1">The numerator.</param><param   
    /// name="n2">The denominator.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Divide", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/DivideResponse")]  
    double Divide(double n1, double n2);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
  
## <a name="see-also"></a>另請參閱
