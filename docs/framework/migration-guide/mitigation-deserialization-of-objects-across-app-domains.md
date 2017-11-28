---
title: "緩和：在應用程式定義域之間還原序列化物件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c42d3274fcb03bc523367ba71c857144b2d78b72
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-deserialization-of-objects-across-app-domains"></a><span data-ttu-id="ba043-102">緩和：在應用程式定義域之間還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="ba043-102">Mitigation: Deserialization of Objects Across App Domains</span></span>
<span data-ttu-id="ba043-103">在某些情況下，當應用程式使用具有不同應用程式基底的兩個或多個應用程式定義域時，嘗試在跨應用程式定義域的邏輯呼叫內容中將物件還原序列化，將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ba043-103">In some cases, when an app uses two or more app domains with different application bases, the attempt to deserialize objects in the logical call context across app domains throws an exception.</span></span>  
  
## <a name="diagnosing-the-issue"></a><span data-ttu-id="ba043-104">診斷問題</span><span class="sxs-lookup"><span data-stu-id="ba043-104">Diagnosing the issue</span></span>  
 <span data-ttu-id="ba043-105">下面這些情況會引發問題：</span><span class="sxs-lookup"><span data-stu-id="ba043-105">The issue arises under the following sequence of conditions:</span></span>  
  
1.  <span data-ttu-id="ba043-106">應用程式使用具有不同應用程式基底的兩個或多個應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="ba043-106">An app uses two or more app domains with different application bases.</span></span>  
  
2.  <span data-ttu-id="ba043-107">某些類型透過呼叫 <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> 或 <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> 這類方法明確加入至 <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="ba043-107">Some types are explicitly added to the <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> by calling a method such as <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> or <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ba043-108">這些類型並未標示為可序列化，而且未儲存在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="ba043-108">These types are not marked as serializable and are not stored in the global assembly cache.</span></span>  
  
3.  <span data-ttu-id="ba043-109">在非預設應用程式定義域中執行的程式碼之後就會嘗試從組態檔讀取值，或使用 XML 將物件還原序列化。</span><span class="sxs-lookup"><span data-stu-id="ba043-109">Later, code running in the non-default app domain tries to read a value from a configuration file or use XML to deserialize an object.</span></span>  
  
4.  <span data-ttu-id="ba043-110">為了要從組態檔讀取或將物件還原序列化，<xref:System.Xml.XmlReader> 物件會嘗試存取組態系統。</span><span class="sxs-lookup"><span data-stu-id="ba043-110">In order to read from a configuration file or deserialize the object, an <xref:System.Xml.XmlReader> object tries to access the configuration system.</span></span>  
  
5.  <span data-ttu-id="ba043-111">如果組態系統尚未初始化，則必須先完成初始化。</span><span class="sxs-lookup"><span data-stu-id="ba043-111">If the configuration system has not already been initialized, it must complete its initialization.</span></span> <span data-ttu-id="ba043-112">這表示，除此之外執行階段還必須為組態系統建立穩定的路徑，它會這樣做：</span><span class="sxs-lookup"><span data-stu-id="ba043-112">This means, among other things, that the runtime has to create a stable path for a configuration system, which it does as follows:</span></span>  
  
    1.  <span data-ttu-id="ba043-113">它會尋找非預設應用程式定義域的辨識項。</span><span class="sxs-lookup"><span data-stu-id="ba043-113">It looks for evidence for the non-default app domain.</span></span>  
  
    2.  <span data-ttu-id="ba043-114">它會根據預設應用程式定義域，嘗試計算非預設應用程式定義域的辨識項。</span><span class="sxs-lookup"><span data-stu-id="ba043-114">It tries to calculate the evidence for the non-default app domain based on the default app domain.</span></span>  
  
    3.  <span data-ttu-id="ba043-115">為了取得預設應用程式定義域的辨識項發出的呼叫，會觸發從非預設應用程式定義域到預設應用程式定義域的跨應用程式定義域呼叫。</span><span class="sxs-lookup"><span data-stu-id="ba043-115">The call to get evidence for the default app domain triggers a cross-app domain call from the non-default app domain to the default app domain.</span></span>  
  
    4.  <span data-ttu-id="ba043-116">在 .NET Framework 的跨應用程式定義域合約中，邏輯呼叫內容中的內容同樣必須跨應用程式定義域的界限進行封送處理。</span><span class="sxs-lookup"><span data-stu-id="ba043-116">As part of the cross-app domain contract in the .NET Framework, the contents of the logical call context also have to be marshaled across app domain boundaries.</span></span>  
  
6.  <span data-ttu-id="ba043-117">由於邏輯呼叫內容中的類型無法在預設應用程式定義域中解析，因此會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ba043-117">Because the types that are in the logical call context cannot be resolved in the default app domain, an exception is thrown.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="ba043-118">緩和</span><span class="sxs-lookup"><span data-stu-id="ba043-118">Mitigation</span></span>  
 <span data-ttu-id="ba043-119">若要解決這個問題，請執行下列動作</span><span class="sxs-lookup"><span data-stu-id="ba043-119">To work around this issue, do the following</span></span>  
  
1.  <span data-ttu-id="ba043-120">尋找擲回例外狀況時，在呼叫堆疊上的 `get_Evidence` 呼叫。</span><span class="sxs-lookup"><span data-stu-id="ba043-120">Look for the call to `get_Evidence` in the call stack when the exception is thrown.</span></span> <span data-ttu-id="ba043-121">例外狀況可以是例外狀況的任一個大型子集，包括 <xref:System.IO.FileNotFoundException> 和 <xref:System.Runtime.Serialization.SerializationException>。</span><span class="sxs-lookup"><span data-stu-id="ba043-121">The exception can be any of a large subset of exceptions, including <xref:System.IO.FileNotFoundException> and <xref:System.Runtime.Serialization.SerializationException>.</span></span>  
  
2.  <span data-ttu-id="ba043-122">找出應用程式中沒有任何物件加入至邏輯呼叫內容的位置，並且加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="ba043-122">Identify the place in the app where no objects are added to the logical call context and add the following code:</span></span>  
  
    ```  
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ba043-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba043-123">See Also</span></span>  
 [<span data-ttu-id="ba043-124">執行階段變更</span><span class="sxs-lookup"><span data-stu-id="ba043-124">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)
