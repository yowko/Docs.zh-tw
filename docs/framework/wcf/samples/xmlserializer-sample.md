---
title: XMLSerializer 範例
ms.date: 03/30/2017
ms.assetid: 7d134453-9a35-4202-ba77-9ca3a65babc3
ms.openlocfilehash: 46f3d10305a244d23be19c87566edacfaf7bff46
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188400"
---
# <a name="xmlserializer-sample"></a><span data-ttu-id="ed31a-102">XMLSerializer 範例</span><span class="sxs-lookup"><span data-stu-id="ed31a-102">XMLSerializer Sample</span></span>
<span data-ttu-id="ed31a-103">這個範例會示範如何序列化和還原序列化與 <xref:System.Xml.Serialization.XmlSerializer> 相容的型別。</span><span class="sxs-lookup"><span data-stu-id="ed31a-103">This sample demonstrates how to serialize and deserialize types that are compatible with the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="ed31a-104">預設的 Windows Communication Foundation (WCF) 格式器是<xref:System.Runtime.Serialization.DataContractSerializer>類別。</span><span class="sxs-lookup"><span data-stu-id="ed31a-104">The default Windows Communication Foundation (WCF) formatter is the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span> <span data-ttu-id="ed31a-105">當無法使用 <xref:System.Xml.Serialization.XmlSerializer> 類別時，<xref:System.Runtime.Serialization.DataContractSerializer> 類別可以用來序列化與還原序列化型別。</span><span class="sxs-lookup"><span data-stu-id="ed31a-105">The <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize and deserialize types when the <xref:System.Runtime.Serialization.DataContractSerializer> class cannot be used.</span></span> <span data-ttu-id="ed31a-106">這時通常需要精確控制 XML，例如，當資料片段必須是 XML 屬性而且不是 XML 項目的情況下。</span><span class="sxs-lookup"><span data-stu-id="ed31a-106">This is often the case when precise control over the XML is required - for example, if a piece of data must be an XML attribute and not an XML element.</span></span> <span data-ttu-id="ed31a-107">此外，<xref:System.Xml.Serialization.XmlSerializer>通常會自動選取時建立的非 WCF 服務用戶端。</span><span class="sxs-lookup"><span data-stu-id="ed31a-107">Also, the <xref:System.Xml.Serialization.XmlSerializer> often gets automatically selected when creating clients for non-WCF services.</span></span>  
  
 <span data-ttu-id="ed31a-108">在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。</span><span class="sxs-lookup"><span data-stu-id="ed31a-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed31a-109">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="ed31a-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ed31a-110"><xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 必須套用至介面，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ed31a-110">The <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.XmlSerializerFormatAttribute> must be applied to the interface as shown in the following sample code.</span></span>  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]  
public interface IXmlSerializerCalculator  
{  
    [OperationContract]  
    ComplexNumber Add(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2);  
}  
```  
  
 <span data-ttu-id="ed31a-111">`ComplexNumber` 類別的 Public 成員會由 <xref:System.Xml.Serialization.XmlSerializer> 序列化成 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="ed31a-111">The public members of `ComplexNumber` class are serialized by <xref:System.Xml.Serialization.XmlSerializer> as XML attributes.</span></span> <span data-ttu-id="ed31a-112"><xref:System.Runtime.Serialization.DataContractSerializer> 無法用來建立這類 XML 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ed31a-112">The <xref:System.Runtime.Serialization.DataContractSerializer> cannot be used to create this kind of XML instance.</span></span>  
  
```csharp  
public class ComplexNumber  
{  
    private double real;  
    private double imaginary;  
  
    [XmlAttribute]  
    public double Real  
    {  
        get { return real; }  
        set { real = value; }  
    }  
  
    [XmlAttribute]  
    public double Imaginary  
    {  
        get { return imaginary; }  
        set { imaginary = value; }  
    }  
  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
    public ComplexNumber()  
    {  
        this.Real = 0;  
        this.Imaginary = 0;  
    }  
  
}  
```  
  
 <span data-ttu-id="ed31a-113">服務實作會計算並傳回適當的結果，即接受並傳回 `ComplexNumber` 型別的值。</span><span class="sxs-lookup"><span data-stu-id="ed31a-113">The service implementation calculates and returns the appropriate result—accepting and returning values of the `ComplexNumber` type.</span></span>  
  
```csharp  
public class XmlSerializerCalculatorService : IXmlSerializerCalculator  
{  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        return new ComplexNumber(n1.Real + n2.Real, n1.Imaginary +  
                                                      n2.Imaginary);  
    }  
    …  
}  
```  
  
 <span data-ttu-id="ed31a-114">用戶端實作也會使用複數。</span><span class="sxs-lookup"><span data-stu-id="ed31a-114">The client implementation also uses complex numbers.</span></span> <span data-ttu-id="ed31a-115">所產生 generatedClient.cs 原始程式檔中定義服務合約和資料類型[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)從服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ed31a-115">Both the service contract and the data types are defined in the generatedClient.cs source file, which was generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="ed31a-116">在這個範例中，Svcutil.exe 能夠偵測合約何時無法由 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化，而還原成發出 `XmlSerializable` 型別。</span><span class="sxs-lookup"><span data-stu-id="ed31a-116">Svcutil.exe can detect when a contract is not serializable by the <xref:System.Runtime.Serialization.DataContractSerializer> and reverts to emitting `XmlSerializable` types in this case.</span></span> <span data-ttu-id="ed31a-117">如果要強制使用 <xref:System.Xml.Serialization.XmlSerializer>，您可以將 /serializer:XmlSerializer (使用 XmlSerializer) 命令選項傳遞至 Svcutil.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="ed31a-117">If you want to force the use of the <xref:System.Xml.Serialization.XmlSerializer>, you can pass the /serializer:XmlSerializer (use XmlSerializer) command option to the Svcutil.exe tool.</span></span>  
  
```csharp  
// Create a client.  
XmlSerializerCalculatorClient client = new  
                         XmlSerializerCalculatorClient();  
  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber();  
value1.Real = 1;  
value1.Imaginary = 2;  
ComplexNumber value2 = new ComplexNumber();  
value2.Real = 3;  
value2.Imaginary = 4;  
ComplexNumber result = client.Add(value1, value2);  
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
    value1.Real, value1.Imaginary, value2.Real, value2.Imaginary,   
    result.Real, result.Imaginary);  
    …  
}  
```  
  
 <span data-ttu-id="ed31a-118">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="ed31a-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ed31a-119">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="ed31a-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 1.41379310344828i  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ed31a-120">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="ed31a-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ed31a-121">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ed31a-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ed31a-122">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="ed31a-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ed31a-123">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ed31a-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ed31a-124">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ed31a-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ed31a-125">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="ed31a-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ed31a-126">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="ed31a-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ed31a-127">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="ed31a-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\XmlSerializer`  
  
## <a name="see-also"></a><span data-ttu-id="ed31a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed31a-128">See Also</span></span>
