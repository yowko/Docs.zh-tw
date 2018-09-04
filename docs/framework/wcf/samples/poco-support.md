---
title: POCO 支援
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: beba1469d5d9575a5b2ef76a4db3747dfcc35d0c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542228"
---
# <a name="poco-support"></a><span data-ttu-id="975fb-102">POCO 支援</span><span class="sxs-lookup"><span data-stu-id="975fb-102">POCO Support</span></span>
<span data-ttu-id="975fb-103">這個範例會示範對未標記型別的序列化支援，此種型別就是尚未套用序列化屬性的型別，有時亦稱為「簡單的 CLR 物件」(Plain Old CLR Object，POCO) 型別。</span><span class="sxs-lookup"><span data-stu-id="975fb-103">This sample demonstrates the serialization support for unmarked types; that is, types to which serialization attributes have not been applied, sometimes referred to as Plain Old CLR Object (POCO) types.</span></span> <span data-ttu-id="975fb-104"><xref:System.Runtime.Serialization.DataContractSerializer> 會對所有具有預設建構函式 (Constructor) 的公用未標記型別推斷資料合約。</span><span class="sxs-lookup"><span data-stu-id="975fb-104">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract for all public unmarked types that have a default constructor.</span></span> <span data-ttu-id="975fb-105">資料合約可以讓您在服務間來回傳遞結構化資料。</span><span class="sxs-lookup"><span data-stu-id="975fb-105">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="975fb-106">如需未標記型別的詳細資訊，請參閱 <<c0> [ 可序列化型別](../../../../docs/framework/wcf/feature-details/serializable-types.md)。</span><span class="sxs-lookup"><span data-stu-id="975fb-106">For more information about unmarked types, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
 <span data-ttu-id="975fb-107">此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)，但會使用複數，而不是基本數字型別。</span><span class="sxs-lookup"><span data-stu-id="975fb-107">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), but uses complex numbers instead of primitive numeric types.</span></span> <span data-ttu-id="975fb-108">它也很類似[Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md)範例，不同之處在於<xref:System.Runtime.Serialization.DataContractAttribute>和<xref:System.Runtime.Serialization.DataMemberAttribute>屬性不會使用。</span><span class="sxs-lookup"><span data-stu-id="975fb-108">It is also similar to the [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md) sample, except that the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are not used.</span></span>  
  
 <span data-ttu-id="975fb-109">服務是由網際網路資訊服務 (IIS) 所裝載，而用戶端是主控台應用程式 (.exe)。</span><span class="sxs-lookup"><span data-stu-id="975fb-109">The service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="975fb-110">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="975fb-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="975fb-111">`ComplexNumber` 類別是在 `ServiceContract` 中使用。</span><span class="sxs-lookup"><span data-stu-id="975fb-111">The `ComplexNumber` class is used in the `ServiceContract`.</span></span> <span data-ttu-id="975fb-112">`ComplexNumber` 型別沒有 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Attribute)，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="975fb-112">The `ComplexNumber` type does not have the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes, as shown in the following sample code.</span></span> <span data-ttu-id="975fb-113">依預設，所有公用屬性 (Property) 和欄位都會經過序列化。</span><span class="sxs-lookup"><span data-stu-id="975fb-113">By default, all public properties and fields are serialized.</span></span>  
  
```  
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="975fb-114">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="975fb-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="975fb-115">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="975fb-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="975fb-116">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="975fb-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="975fb-117">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="975fb-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="975fb-118">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="975fb-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="975fb-119">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="975fb-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="975fb-120">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="975fb-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="975fb-121">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="975fb-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a><span data-ttu-id="975fb-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="975fb-122">See Also</span></span>  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 [<span data-ttu-id="975fb-123">可序列化類型</span><span class="sxs-lookup"><span data-stu-id="975fb-123">Serializable Types</span></span>](../../../../docs/framework/wcf/feature-details/serializable-types.md)
