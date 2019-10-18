---
title: 最佳做法：媒介
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: a7c037b5942a404b1ff790638979a8e430394151
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320791"
---
# <a name="best-practices-intermediaries"></a><span data-ttu-id="90856-102">最佳做法：媒介</span><span class="sxs-lookup"><span data-stu-id="90856-102">Best Practices: Intermediaries</span></span>
<span data-ttu-id="90856-103">當呼叫媒介時必須務必注意地正確處理錯誤，以確認媒介的服務端通道有正常關閉。</span><span class="sxs-lookup"><span data-stu-id="90856-103">Care must be taken to handle faults correctly when calling intermediaries to make sure service side channels on the intermediary are closed properly.</span></span>  
  
 <span data-ttu-id="90856-104">請考慮下列狀況。</span><span class="sxs-lookup"><span data-stu-id="90856-104">Consider the following scenario.</span></span> <span data-ttu-id="90856-105">用戶端呼叫之後會呼叫後端服務的媒介。</span><span class="sxs-lookup"><span data-stu-id="90856-105">A client makes a call to an intermediary which then calls a back-end service.</span></span>  <span data-ttu-id="90856-106">後端服務未定義錯誤合約，因此，任何由該服務擲回的錯誤將被視為不具型別的錯誤。</span><span class="sxs-lookup"><span data-stu-id="90856-106">The back-end service defines no fault contract, so any fault thrown from that service will be treated as an un-typed fault.</span></span>  <span data-ttu-id="90856-107">後端服務會擲回 <xref:System.ApplicationException>，而 WCF 會正確中止服務端通道。</span><span class="sxs-lookup"><span data-stu-id="90856-107">The back-end service throws an <xref:System.ApplicationException> and WCF correctly aborts the service-side channel.</span></span> <span data-ttu-id="90856-108"><xref:System.ApplicationException> 呈現為擲回媒介的 <xref:System.ServiceModel.FaultException>。</span><span class="sxs-lookup"><span data-stu-id="90856-108">The <xref:System.ApplicationException> then surfaces as a <xref:System.ServiceModel.FaultException> that is thrown to the intermediary.</span></span> <span data-ttu-id="90856-109">媒介重新擲回 <xref:System.ApplicationException>。</span><span class="sxs-lookup"><span data-stu-id="90856-109">The intermediary re-throws the <xref:System.ApplicationException>.</span></span> <span data-ttu-id="90856-110">WCF 將此解譯為由媒介產生之不具型別的錯誤，並轉送至用戶端上。</span><span class="sxs-lookup"><span data-stu-id="90856-110">WCF interprets this as an un-typed fault from the intermediary and forwards it on to the client.</span></span> <span data-ttu-id="90856-111">當接收錯誤之後，媒介與用戶端皆會尋找其用戶端通道之錯誤。</span><span class="sxs-lookup"><span data-stu-id="90856-111">Upon receiving the fault, both the intermediary and the client fault their client-side channels.</span></span> <span data-ttu-id="90856-112">然而，媒介的服務端通道仍然會開啟，因為 WCF 不知道該錯誤是嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="90856-112">The intermediary’s service-side channel however remains open because WCF doesn’t know the fault is fatal.</span></span>  
  
 <span data-ttu-id="90856-113">此狀況的最佳作法是偵測來自服務的錯誤是否為嚴重錯誤，若是，媒介應尋找其服務端通道之錯誤，如下列程式碼片段所示。</span><span class="sxs-lookup"><span data-stu-id="90856-113">The best practice in this scenario is to detect if the fault coming from the service is fatal and if so the intermediary should fault its service-side channel as shown in the following code snippet.</span></span>  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="90856-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="90856-114">See also</span></span>

- [<span data-ttu-id="90856-115">WCF 錯誤處理</span><span class="sxs-lookup"><span data-stu-id="90856-115">WCF Error Handling</span></span>](wcf-error-handling.md)
- [<span data-ttu-id="90856-116">指定及處理合約與服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="90856-116">Specifying and Handling Faults in Contracts and Services</span></span>](specifying-and-handling-faults-in-contracts-and-services.md)
