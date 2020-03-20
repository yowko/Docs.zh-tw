---
title: XmlSerializer 錯誤
ms.date: 03/30/2017
ms.assetid: c6b80f14-64f4-4162-ae76-71664cf42fd3
ms.openlocfilehash: adb14fdb45aa71bbaf4585cbfba55059df7cddf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183159"
---
# <a name="xmlserializer-faults"></a><span data-ttu-id="c2b49-102">XmlSerializer 錯誤</span><span class="sxs-lookup"><span data-stu-id="c2b49-102">XmlSerializer Faults</span></span>
<span data-ttu-id="c2b49-103"><xref:System.Xml.Serialization.XmlSerializer> 錯誤合約範例會使用 <xref:System.Xml.Serialization.XmlSerializer> 示範如何在服務與用戶端之間傳達錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="c2b49-103">The <xref:System.Xml.Serialization.XmlSerializer> fault contract sample demonstrates how to communicate error information from a service to a client using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="c2b49-104">該示例基於[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，並將一些附加代碼添加到服務中，以將內部異常轉換為故障。</span><span class="sxs-lookup"><span data-stu-id="c2b49-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="c2b49-105">用戶端會嘗試執行除數為零，以便強制在服務上造成錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="c2b49-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2b49-106">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="c2b49-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c2b49-107">計算機合約已修改成包含 <xref:System.ServiceModel.FaultContractAttribute>，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="c2b49-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span> <span data-ttu-id="c2b49-108">此外，<xref:System.ServiceModel.XmlSerializerFormatAttribute> 是用來以 <xref:System.Xml.Serialization.XmlSerializer> 啟用序列化 (Serialization)。</span><span class="sxs-lookup"><span data-stu-id="c2b49-108">Also, the <xref:System.ServiceModel.XmlSerializerFormatAttribute> is used to enable serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="c2b49-109">此屬性 (Attribute) 上的 <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A> 屬性 (Property) 設為 `true`，指示序列化程式使用 <xref:System.Xml.Serialization.XmlSerializer> 來讀取和寫入錯誤。</span><span class="sxs-lookup"><span data-stu-id="c2b49-109">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A> property is set to `true` on this attribute, which instructs the serializer to use the <xref:System.Xml.Serialization.XmlSerializer> for reading and writing faults.</span></span>  
  
```csharp
[XmlSerializerFormat(SupportFaults=true)]  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
  
    [OperationContract]  
    int Subtract(int n1, int n2);  
  
    [OperationContract]  
    int Multiply(int n1, int n2);  
  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 <span data-ttu-id="c2b49-110">生成用戶端代理的代碼時，必須將 **/use 序列化器 ForFaults**標誌應用於[服務模型中繼資料實用程式工具 （Svcutil.exe）。](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)</span><span class="sxs-lookup"><span data-stu-id="c2b49-110">When generating code for the client proxy, you must apply the **/UseSerializerForFaults** flag to [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c2b49-111">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="c2b49-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c2b49-112">確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="c2b49-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c2b49-113">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="c2b49-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c2b49-114">要在單機或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。</span><span class="sxs-lookup"><span data-stu-id="c2b49-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c2b49-115">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="c2b49-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c2b49-116">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="c2b49-116">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c2b49-117">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="c2b49-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c2b49-118">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="c2b49-118">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\XmlSerializerFaults`  
  
## <a name="see-also"></a><span data-ttu-id="c2b49-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2b49-119">See also</span></span>

- <xref:System.ServiceModel.XmlSerializerFormatAttribute>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A>
