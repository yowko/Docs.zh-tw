---
title: 自訂 WSDL 發行物
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: cc0731276fcf9178403fd434e03a0666d11ac1f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953586"
---
# <a name="custom-wsdl-publication"></a><span data-ttu-id="a466a-102">自訂 WSDL 發行物</span><span class="sxs-lookup"><span data-stu-id="a466a-102">Custom WSDL Publication</span></span>
<span data-ttu-id="a466a-103">這個範例會示範如何：</span><span class="sxs-lookup"><span data-stu-id="a466a-103">This sample demonstrates how to:</span></span>  
  
- <span data-ttu-id="a466a-104">實作自訂 <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> 屬性 (Attribute) 上的 <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>，以便將屬性 (Attribute) 的屬性 (Property) 匯出為 WSDL 附註。</span><span class="sxs-lookup"><span data-stu-id="a466a-104">Implement a <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> on a custom <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> attribute to export attribute properties as WSDL annotations.</span></span>  
  
- <span data-ttu-id="a466a-105">實作 <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> 以匯入自訂 WSDL 附註。</span><span class="sxs-lookup"><span data-stu-id="a466a-105">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> to import the custom WSDL annotations.</span></span>  
  
- <span data-ttu-id="a466a-106">在自訂合約行為和自訂作業行為上分別實作 <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> 和 <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType>，將匯入的附註寫入為 CodeDOM 中的註解，以用於匯入的合約和作業。</span><span class="sxs-lookup"><span data-stu-id="a466a-106">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> on a custom contract behavior and a custom operation behavior, respectively, to write imported annotations as comments in the CodeDom for the imported contract and operation.</span></span>  
  
- <span data-ttu-id="a466a-107">使用下載 wsdl <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> 、使用自訂<xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> wsdl 匯入工具匯入 wsdl, 以及在和中C#產生具有 wsdl 附注的 Windows Communication Foundation (WCF) 用戶端程式代碼做為///和 ' ' ' 批註<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType>Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="a466a-107">Use the <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> to download the WSDL, a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> to import the WSDL using the custom WSDL importer, and the <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> to generate Windows Communication Foundation (WCF) client code with the WSDL annotations as /// and ''' comments in C# and Visual Basic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a466a-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="a466a-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="a466a-109">服務</span><span class="sxs-lookup"><span data-stu-id="a466a-109">Service</span></span>  
 <span data-ttu-id="a466a-110">在這個範例中，會使用兩個自訂屬性來標示服務。</span><span class="sxs-lookup"><span data-stu-id="a466a-110">The service in this sample is marked with two custom attributes.</span></span> <span data-ttu-id="a466a-111">第一個是 `WsdlDocumentationAttribute`，它會在建構函式中接受字串，您可以套用此屬性來為合約介面或作業提供描述其使用方式的字串。</span><span class="sxs-lookup"><span data-stu-id="a466a-111">The first, the `WsdlDocumentationAttribute`, accepts a string in the constructor and can be applied to provide a contract interface or operation with a string that describes its usage.</span></span> <span data-ttu-id="a466a-112">第二個是 `WsdlParamOrReturnDocumentationAttribute`，您可以將它套用至傳回值或參數，在作業中描述這些值。</span><span class="sxs-lookup"><span data-stu-id="a466a-112">The second, `WsdlParamOrReturnDocumentationAttribute`, can be applied to return values or parameters to describe those values in the operation.</span></span> <span data-ttu-id="a466a-113">下列範例示範使用這些屬性所描述的服務合約 `ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="a466a-113">The following example shows a service contract, `ICalculator`, described using these attributes.</span></span>  
  
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
  
 <span data-ttu-id="a466a-114">`WsdlDocumentationAttribute` 會實作 <xref:System.ServiceModel.Description.IContractBehavior> 和 <xref:System.ServiceModel.Description.IOperationBehavior>，以便在開啟服務時將屬性執行個體新增至對應的 <xref:System.ServiceModel.Description.ContractDescription> 或 <xref:System.ServiceModel.Description.OperationDescription>。</span><span class="sxs-lookup"><span data-stu-id="a466a-114">The `WsdlDocumentationAttribute` implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior>, so the attribute instances are added to the corresponding <xref:System.ServiceModel.Description.ContractDescription> or <xref:System.ServiceModel.Description.OperationDescription> when the service is opened.</span></span> <span data-ttu-id="a466a-115">這個屬性還會實作 <xref:System.ServiceModel.Description.IWsdlExportExtension>。</span><span class="sxs-lookup"><span data-stu-id="a466a-115">The attribute also implements <xref:System.ServiceModel.Description.IWsdlExportExtension>.</span></span> <span data-ttu-id="a466a-116">呼叫 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> 時，會傳入用來匯出中繼資料的 <xref:System.ServiceModel.Description.WsdlExporter> 和含有服務描述物件的 <xref:System.ServiceModel.Description.WsdlContractConversionContext> 做為參數，以啟用匯出之中繼資料的修改作業。</span><span class="sxs-lookup"><span data-stu-id="a466a-116">When <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> is called, the <xref:System.ServiceModel.Description.WsdlExporter> that is used to export the metadata and the <xref:System.ServiceModel.Description.WsdlContractConversionContext> that contains the service description objects are passed in as parameters enabling the modification of the exported metadata.</span></span>  
  
 <span data-ttu-id="a466a-117">在這個範例中，會依據匯出的內容物件是否含有 <xref:System.ServiceModel.Description.ContractDescription> 或 <xref:System.ServiceModel.Description.OperationDescription> 而定，從使用文字屬性 (Property) 的屬性 (Attribute) 擷取註解，並將它新增至 WSDL 附註項目，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="a466a-117">In this sample, depending upon whether the export context object has a <xref:System.ServiceModel.Description.ContractDescription> or an <xref:System.ServiceModel.Description.OperationDescription>, a comment is extracted from the attribute using the text property and is added to the WSDL annotation element as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="a466a-118">如果是要匯出某項作業，這個範例會使用反映 (Reflection) 來為參數和傳回值取得任何 `WsdlParamOrReturnDocumentationAttribute` 值，並將它們新增至該作業的 WSDL 附註項目，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a466a-118">If an operation is being exported, the sample uses reflection to obtain any `WsdlParamOrReturnDocumentationAttribute` values for parameters and return values and adds them to the WSDL annotation elements for that operation as follows.</span></span>  
  
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
  
 <span data-ttu-id="a466a-119">這個範例會接著使用下列組態檔，以標準方式發行中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a466a-119">The sample then publishes metadata in the standard way, using the following configuration file.</span></span>  
  
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
  
## <a name="svcutil-client"></a><span data-ttu-id="a466a-120">Svcutil 用戶端</span><span class="sxs-lookup"><span data-stu-id="a466a-120">Svcutil client</span></span>  
 <span data-ttu-id="a466a-121">這個範例不使用 Svcutil.exe。</span><span class="sxs-lookup"><span data-stu-id="a466a-121">This sample does not use Svcutil.exe.</span></span> <span data-ttu-id="a466a-122">這個範例會在 generatedClient.cs 檔案中提供合約，以便在示範自訂 WSDL 匯入作業與程式碼產生作業之後叫用服務。</span><span class="sxs-lookup"><span data-stu-id="a466a-122">The contract is provided in the generatedClient.cs file so that after the sample demonstrates custom WSDL import and code generation, the service can be invoked.</span></span> <span data-ttu-id="a466a-123">若要在這個範例中使用下列自訂 WSDL 匯入工具，您可以執行 Svcutil.exe，並指定 `/svcutilConfig` 選項，來提供此範例 (其參考 `WsdlDocumentation.dll` 程式庫) 中所使用之用戶端組態檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="a466a-123">To use the following custom WSDL importer for this example, you can run Svcutil.exe and specify the `/svcutilConfig` option, giving the path to the client configuration file used in this sample, which references the `WsdlDocumentation.dll` library.</span></span> <span data-ttu-id="a466a-124">不過，若要載入 `WsdlDocumentationImporter`，Svuctil.exe 就必須能夠找到並載入 `WsdlDocumentation.dll` 程式庫，這表示應先在全域組件快取中、路徑中或是在包含 Svcutil.exe 的同一個目錄中註冊此程式庫。</span><span class="sxs-lookup"><span data-stu-id="a466a-124">To load the `WsdlDocumentationImporter`, however, Svuctil.exe must be able to locate and load the `WsdlDocumentation.dll` library, which means either that it is registered in the global assembly cache, in the path, or is in the same directory as Svcutil.exe.</span></span> <span data-ttu-id="a466a-125">對於像這樣的基本範例，最簡單的方式就是將 Svcutil.exe 和用戶端組態檔複製到 `WsdlDocumentation.dll` 所在的相同目錄中，再從那裡加以執行。</span><span class="sxs-lookup"><span data-stu-id="a466a-125">For a basic sample such as this, the easiest thing to do is to copy Svcutil.exe and the client configuration file into the same directory as `WsdlDocumentation.dll` and run it from there.</span></span>  
  
## <a name="the-custom-wsdl-importer"></a><span data-ttu-id="a466a-126">自訂 WSDL 匯入工具</span><span class="sxs-lookup"><span data-stu-id="a466a-126">The Custom WSDL Importer</span></span>  
 <span data-ttu-id="a466a-127">自訂的 <xref:System.ServiceModel.Description.IWsdlImportExtension> 物件 `WsdlDocumentationImporter` 也會實作 <xref:System.ServiceModel.Description.IContractBehavior> 和 <xref:System.ServiceModel.Description.IOperationBehavior> (要新增至匯入的 ServiceEndpoints)，以及 <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> 和 <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> (會在建立合約或作業程式碼時被叫用來修改程式碼產生)。</span><span class="sxs-lookup"><span data-stu-id="a466a-127">The custom <xref:System.ServiceModel.Description.IWsdlImportExtension> object `WsdlDocumentationImporter` also implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior> to be added to the imported ServiceEndpoints and <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> to be invoked to modify the code generation when the contract or operation code is being created.</span></span>  
  
 <span data-ttu-id="a466a-128">在 <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> 方法中，這個範例首先會判斷 WSDL 附註是在合約層級還是在作業層級，然後在適當的範圍內將本身新增為行為，並傳遞匯入的附註文字至其建構函式。</span><span class="sxs-lookup"><span data-stu-id="a466a-128">First, in the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method, the sample determines whether the WSDL annotation is at the contract or operation level, and adds itself as a behavior at the appropriate scope, passing the imported annotation text to its constructor.</span></span>  
  
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
  
 <span data-ttu-id="a466a-129">接下來，系統會在產生程式碼時叫用 <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> 和 <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> 方法，並傳遞適當的內容資訊。</span><span class="sxs-lookup"><span data-stu-id="a466a-129">Then, when the code is generated, the system invokes the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> methods, passing the appropriate context information.</span></span> <span data-ttu-id="a466a-130">這個範例會格式化自訂 WSDL 附註，再將它們當做註解插入 CodeDom 中。</span><span class="sxs-lookup"><span data-stu-id="a466a-130">The sample formats the custom WSDL annotations and inserts them as comments into the CodeDom.</span></span>  
  
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
  
## <a name="the-client-application"></a><span data-ttu-id="a466a-131">用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="a466a-131">The Client Application</span></span>  
 <span data-ttu-id="a466a-132">用戶端應用程式會在應用程式組態檔中指定自訂 WSDL 匯入工具來加以載入。</span><span class="sxs-lookup"><span data-stu-id="a466a-132">The client application loads the custom WSDL importer by specifying it in the application configuration file.</span></span>  
  
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
  
 <span data-ttu-id="a466a-133">一旦指定了自訂匯入工具, WCF 中繼資料系統就會將自訂<xref:System.ServiceModel.Description.WsdlImporter>匯入工具載入至任何針對該用途所建立的。</span><span class="sxs-lookup"><span data-stu-id="a466a-133">Once the custom importer has been specified, the WCF metadata system loads the custom importer into any <xref:System.ServiceModel.Description.WsdlImporter> created for that purpose.</span></span> <span data-ttu-id="a466a-134">這個範例會使用 <xref:System.ServiceModel.Description.MetadataExchangeClient> 來下載中繼資料、使用已正確設定的 <xref:System.ServiceModel.Description.WsdlImporter> 以使用範例所建立之自訂匯入工具來匯入中繼資料，以及使用 <xref:System.ServiceModel.Description.ServiceContractGenerator> 將修改的合約資訊編譯成 Visual Basic 和 C# 用戶端程式碼，此程式碼可以用於 Visual Studio 以支援 Intellisense，也可以編譯為 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="a466a-134">This sample uses the <xref:System.ServiceModel.Description.MetadataExchangeClient> to download the metadata, the <xref:System.ServiceModel.Description.WsdlImporter> properly configured to import the metadata using the custom importer the sample creates, and the <xref:System.ServiceModel.Description.ServiceContractGenerator> to compile the modified contract information into both Visual Basic and C# client code that can be used in Visual Studio to support Intellisense or compiled into XML documentation.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a466a-135">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="a466a-135">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a466a-136">請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="a466a-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a466a-137">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="a466a-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a466a-138">若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="a466a-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a466a-139">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="a466a-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a466a-140">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="a466a-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a466a-141">如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。</span><span class="sxs-lookup"><span data-stu-id="a466a-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a466a-142">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="a466a-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
