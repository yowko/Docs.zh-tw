---
title: WCF 錯誤處理
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: 90c1d5a955de10b7e65dd21bda7ebfb64f24399d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504912"
---
# <a name="wcf-error-handling"></a><span data-ttu-id="e88b8-102">WCF 錯誤處理</span><span class="sxs-lookup"><span data-stu-id="e88b8-102">WCF Error Handling</span></span>
<span data-ttu-id="e88b8-103">WCF 應用程式遇到的錯誤屬於下列其中一個群組：</span><span class="sxs-lookup"><span data-stu-id="e88b8-103">The errors encountered by a WCF application belong to one of three groups:</span></span>  
  
1.  <span data-ttu-id="e88b8-104">通訊錯誤</span><span class="sxs-lookup"><span data-stu-id="e88b8-104">Communication Errors</span></span>  
  
2.  <span data-ttu-id="e88b8-105">Proxy/通道錯誤</span><span class="sxs-lookup"><span data-stu-id="e88b8-105">Proxy/Channel Errors</span></span>  
  
3.  <span data-ttu-id="e88b8-106">應用程式錯誤</span><span class="sxs-lookup"><span data-stu-id="e88b8-106">Application Errors</span></span>  
  
 <span data-ttu-id="e88b8-107">當網路無法使用、用戶端使用不正確的位址，或者服務主機並未接聽傳入訊息時，就會發生通訊錯誤。</span><span class="sxs-lookup"><span data-stu-id="e88b8-107">Communication errors occur when a network is unavailable, a client uses an incorrect address, or the service host is not listening for incoming messages.</span></span> <span data-ttu-id="e88b8-108">這種類型的錯誤會當做 <xref:System.ServiceModel.CommunicationException> 或 <xref:System.ServiceModel.CommunicationException> 衍生的類別傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="e88b8-108">Errors of this type are returned to the client as <xref:System.ServiceModel.CommunicationException> or <xref:System.ServiceModel.CommunicationException>-derived classes.</span></span>  
  
 <span data-ttu-id="e88b8-109">Proxy/通道錯誤是指發生在通道或 Proxy 本身內部的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e88b8-109">Proxy/Channel errors are errors that occur within the channel or proxy itself.</span></span> <span data-ttu-id="e88b8-110">這種類型的錯誤包括：嘗試使用已經關閉的 Proxy 或通道、用戶端與服務之間存在合約不符，或者服務拒絕了用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="e88b8-110">Errors of this type include: attempting to use a proxy or channel that has been closed, a contract mismatch exists between the client and service, or the client’s credentials are rejected by the service.</span></span> <span data-ttu-id="e88b8-111">還有許多不同類型的錯誤屬於此分類，但是數目太多無法在此列出。</span><span class="sxs-lookup"><span data-stu-id="e88b8-111">There are many different types of errors in this category, too many to list here.</span></span> <span data-ttu-id="e88b8-112">這種類型的錯誤會依現狀傳回給用戶端 (不在例外狀況物件上執行任何轉換)。</span><span class="sxs-lookup"><span data-stu-id="e88b8-112">Errors of this type are returned to the client as-is (no transformation is performed on the exception objects).</span></span>  
  
 <span data-ttu-id="e88b8-113">應用程式錯誤會在服務作業執行期間發生。</span><span class="sxs-lookup"><span data-stu-id="e88b8-113">Application errors occur during the execution of a service operation.</span></span> <span data-ttu-id="e88b8-114">這種類型的錯誤會當做 <xref:System.ServiceModel.FaultException> 或 <xref:System.ServiceModel.FaultException%601> 傳送至用戶端。</span><span class="sxs-lookup"><span data-stu-id="e88b8-114">Errors of this kind are sent to the client as <xref:System.ServiceModel.FaultException> or <xref:System.ServiceModel.FaultException%601>.</span></span>  
  
 <span data-ttu-id="e88b8-115">WCF 中的錯誤處理包括下列其中一種或多種執行方式：</span><span class="sxs-lookup"><span data-stu-id="e88b8-115">Error handling in WCF is performed by one or more of the following:</span></span>  
  
-   <span data-ttu-id="e88b8-116">直接處理擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e88b8-116">Directly handling the exception thrown.</span></span> <span data-ttu-id="e88b8-117">系統只會針對通訊和 Proxy/通道錯誤進行這種處理方式。</span><span class="sxs-lookup"><span data-stu-id="e88b8-117">This is only done for communication and proxy/channel errors.</span></span>  
  
-   <span data-ttu-id="e88b8-118">使用錯誤合約</span><span class="sxs-lookup"><span data-stu-id="e88b8-118">Using fault contracts</span></span>  
  
-   <span data-ttu-id="e88b8-119">實作 <xref:System.ServiceModel.Dispatcher.IErrorHandler> 介面</span><span class="sxs-lookup"><span data-stu-id="e88b8-119">Implementing the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface</span></span>  
  
-   <span data-ttu-id="e88b8-120">處理 <xref:System.ServiceModel.ServiceHost> 事件</span><span class="sxs-lookup"><span data-stu-id="e88b8-120">Handling <xref:System.ServiceModel.ServiceHost> events</span></span>  
  
## <a name="fault-contracts"></a><span data-ttu-id="e88b8-121">錯誤合約</span><span class="sxs-lookup"><span data-stu-id="e88b8-121">Fault Contracts</span></span>  
 <span data-ttu-id="e88b8-122">錯誤合約可讓您以獨立於平台的方式定義服務作業期間可能會發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e88b8-122">Fault contracts allow you to define the errors that can occur during service operation in a platform independent way.</span></span> <span data-ttu-id="e88b8-123">根據預設，從服務作業內部擲回的所有例外狀況都會當做 <xref:System.ServiceModel.FaultException> 物件傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="e88b8-123">By default all exceptions thrown from within a service operation will be returned to the client as a <xref:System.ServiceModel.FaultException> object.</span></span> <span data-ttu-id="e88b8-124"><xref:System.ServiceModel.FaultException> 物件所包含的資訊非常少。</span><span class="sxs-lookup"><span data-stu-id="e88b8-124">The <xref:System.ServiceModel.FaultException> object will contain very little information.</span></span> <span data-ttu-id="e88b8-125">您可以定義錯誤合約並將錯誤當做 <xref:System.ServiceModel.FaultException%601> 傳回，藉以控制傳送至用戶端的資訊。</span><span class="sxs-lookup"><span data-stu-id="e88b8-125">You can control the information sent to the client by defining a fault contract and returning the error as a <xref:System.ServiceModel.FaultException%601>.</span></span> <span data-ttu-id="e88b8-126">如需詳細資訊，請參閱[指定與處理合約和服務中的錯誤](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e88b8-126">For more information, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
## <a name="ierrorhandler"></a><span data-ttu-id="e88b8-127">IErrorHandler</span><span class="sxs-lookup"><span data-stu-id="e88b8-127">IErrorHandler</span></span>  
 <span data-ttu-id="e88b8-128"><xref:System.ServiceModel.Dispatcher.IErrorHandler> 介面可讓您進一步控制 WCF 應用程式如何回應錯誤。</span><span class="sxs-lookup"><span data-stu-id="e88b8-128">The <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface allows you more control over how your WCF application responds to errors.</span></span>  <span data-ttu-id="e88b8-129">它不僅能讓您完全控制傳送至用戶端的錯誤訊息，還能讓您執行自訂錯誤處理，例如記錄。</span><span class="sxs-lookup"><span data-stu-id="e88b8-129">It gives you full control over the fault message that is returned to the client and allows you to perform custom error processing such as logging.</span></span>  <span data-ttu-id="e88b8-130">如需有關<xref:System.ServiceModel.Dispatcher.IErrorHandler>和[擴充控制透過錯誤處理和報告](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)</span><span class="sxs-lookup"><span data-stu-id="e88b8-130">For more information about <xref:System.ServiceModel.Dispatcher.IErrorHandler> and [Extending Control Over Error Handling and Reporting](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)</span></span>  
  
## <a name="servicehost-events"></a><span data-ttu-id="e88b8-131">ServiceHost 事件</span><span class="sxs-lookup"><span data-stu-id="e88b8-131">ServiceHost Events</span></span>  
 <span data-ttu-id="e88b8-132"><xref:System.ServiceModel.ServiceHost> 類別會裝載服務並定義許多處理錯誤可能需要的事件。</span><span class="sxs-lookup"><span data-stu-id="e88b8-132">The <xref:System.ServiceModel.ServiceHost> class hosts services and defines several events that may be needed for handling errors.</span></span> <span data-ttu-id="e88b8-133">例如: </span><span class="sxs-lookup"><span data-stu-id="e88b8-133">For example:</span></span>  
  
1.  <!--zz <xref:System.ServiceModel.ServiceHost.Faulted>-->  `System.ServiceModel.ServiceHost.Faulted`
  
2. <!--zz  <xref:System.ServiceModel.ServiceHost.UnknownMessageReceived>  --> `System.ServiceModel.ServiceHost.UnknownMessageReceived`
  
 <span data-ttu-id="e88b8-134">如需詳細資訊，請參閱<xref:System.ServiceModel.ServiceHost>。</span><span class="sxs-lookup"><span data-stu-id="e88b8-134">For more information, see <xref:System.ServiceModel.ServiceHost></span></span>
