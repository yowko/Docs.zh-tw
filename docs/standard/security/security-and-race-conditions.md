---
title: "安全性和競爭情形"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c092113f670c5799d98dcb13c9c713bbd1a47fb6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="05c83-102">安全性和競爭情形</span><span class="sxs-lookup"><span data-stu-id="05c83-102">Security and Race Conditions</span></span>
<span data-ttu-id="05c83-103">值得注意的另一個部分是利用競爭情形的安全性漏洞的可能性。</span><span class="sxs-lookup"><span data-stu-id="05c83-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="05c83-104">有幾種的方式可能造成此。</span><span class="sxs-lookup"><span data-stu-id="05c83-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="05c83-105">請依照下列子主題簡述一些主要開發人員必須避免的陷阱。</span><span class="sxs-lookup"><span data-stu-id="05c83-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="05c83-106">Dispose 方法中的競爭情形</span><span class="sxs-lookup"><span data-stu-id="05c83-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="05c83-107">如果類別的**處置**方法 (如需詳細資訊，請參閱[回收](../../../docs/standard/garbage-collection/index.md)) 是未同步處理，則可能該的清除程式碼內**處置**可以執行多個一次，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="05c83-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
```  
  
```csharp  
void Dispose()   
{  
    if( myObj != null )   
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 <span data-ttu-id="05c83-108">因為這**處置**實作未同步處理，就可能`Cleanup`由第一個執行緒，然後才能在第二個執行緒呼叫`_myObj`設**null**。</span><span class="sxs-lookup"><span data-stu-id="05c83-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="05c83-109">是否有安全性考量而定會發生什麼事時`Cleanup`程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="05c83-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="05c83-110">未同步處理的主要問題**處置**實作牽涉到的資源控制代碼，例如檔案使用。</span><span class="sxs-lookup"><span data-stu-id="05c83-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="05c83-111">處理不當，可能會導致錯誤使用控制代碼，這通常會導致安全性弱點。</span><span class="sxs-lookup"><span data-stu-id="05c83-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="05c83-112">建構函式中的競爭情形</span><span class="sxs-lookup"><span data-stu-id="05c83-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="05c83-113">在某些應用程式，它可能會完全執行其類別建構函式 」 之前存取類別成員的其他執行緒。</span><span class="sxs-lookup"><span data-stu-id="05c83-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="05c83-114">您應該檢閱以確定沒有任何安全性問題如果此事件應該會發生，還是有必要，同步處理執行緒的所有類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="05c83-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="05c83-115">快取物件的競爭情形</span><span class="sxs-lookup"><span data-stu-id="05c83-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="05c83-116">快取安全性資訊或使用程式碼存取安全性的程式碼[Assert](../../../docs/framework/misc/using-the-assert-method.md)作業可能也會很容易競爭如果未適當地同步處理類別的其他部分，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="05c83-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False()  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
```  
  
```csharp  
void SomeSecureFunction()   
{  
    if(SomeDemandPasses())   
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false();  
    }  
}  
void DoOtherWork()   
{  
    if( fCallersOK )   
    {  
        DoSomethingTrusted();  
    }  
    else   
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
 <span data-ttu-id="05c83-117">如果沒有其他路徑`DoOtherWork`可從另一個執行緒使用相同的物件進行呼叫，不受信任的呼叫端可以略過需求。</span><span class="sxs-lookup"><span data-stu-id="05c83-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="05c83-118">如果您的程式碼會快取的安全性資訊，請確定它檢閱此弱點。</span><span class="sxs-lookup"><span data-stu-id="05c83-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="05c83-119">完成項中的競爭情形</span><span class="sxs-lookup"><span data-stu-id="05c83-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="05c83-120">物件，參考的靜態或未受管理的資源，然後釋放其完成項中也可能會發生競爭情形。</span><span class="sxs-lookup"><span data-stu-id="05c83-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="05c83-121">如果多個物件共用資源的操作中類別的完成項，則物件必須同步處理所有對該資源的存取。</span><span class="sxs-lookup"><span data-stu-id="05c83-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05c83-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05c83-122">See Also</span></span>  
 [<span data-ttu-id="05c83-123">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="05c83-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
