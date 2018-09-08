---
title: 安全性和競爭情形
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57ceaedc7c38ae70a0db5a7fd584a765a7474aff
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210490"
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="215b8-102">安全性和競爭情形</span><span class="sxs-lookup"><span data-stu-id="215b8-102">Security and Race Conditions</span></span>
<span data-ttu-id="215b8-103">值得注意的另一個部分是利用競爭條件安全性漏洞的可能性。</span><span class="sxs-lookup"><span data-stu-id="215b8-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="215b8-104">有數種方式，這可能發生。</span><span class="sxs-lookup"><span data-stu-id="215b8-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="215b8-105">請依照下列子主題說明一些主要的開發人員必須避免的陷阱。</span><span class="sxs-lookup"><span data-stu-id="215b8-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="215b8-106">Dispose 方法中的競爭情形</span><span class="sxs-lookup"><span data-stu-id="215b8-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="215b8-107">如果類別的**處置**方法 (如需詳細資訊，請參閱[回收](../../../docs/standard/garbage-collection/index.md)) 是未同步處理，就可以在該清除程式碼**處置**可以執行多個一次，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="215b8-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
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
    if (myObj != null)   
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 <span data-ttu-id="215b8-108">因為這**處置**實作未同步處理，就可能`Cleanup`由第一個執行緒，然後第二個執行緒呼叫`_myObj`設定為**null**。</span><span class="sxs-lookup"><span data-stu-id="215b8-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="215b8-109">這是否有安全性考量而定會發生什麼事時`Cleanup`程式碼隨即執行。</span><span class="sxs-lookup"><span data-stu-id="215b8-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="215b8-110">未同步處理的主要問題**處置**實作牽涉到的資源控制代碼，例如檔案使用。</span><span class="sxs-lookup"><span data-stu-id="215b8-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="215b8-111">處理不當，可能會導致錯誤控制代碼使用，通常會導致安全性弱點。</span><span class="sxs-lookup"><span data-stu-id="215b8-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="215b8-112">建構函式中的競爭情形</span><span class="sxs-lookup"><span data-stu-id="215b8-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="215b8-113">在某些應用程式，它可能會供其他執行緒來存取類別成員，才能完全執行其類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="215b8-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="215b8-114">您應該再次檢查以確定沒有任何安全性問題如果這應該會發生，或如有必要，同步處理執行緒的所有類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="215b8-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="215b8-115">使用快取物件的競爭情形</span><span class="sxs-lookup"><span data-stu-id="215b8-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="215b8-116">程式碼會快取安全性資訊，或是使用程式碼存取安全性[Assert](../../../docs/framework/misc/using-the-assert-method.md)作業可能也會很容易的競爭情形如果未適當地同步處理類別的其他部分，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="215b8-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False  
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
    if (SomeDemandPasses())   
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false;  
    }  
}  
void DoOtherWork()   
{  
    if (fCallersOK)   
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
  
 <span data-ttu-id="215b8-117">如果有其他路徑`DoOtherWork`，可以從相同的物件與另一個執行緒呼叫，不受信任的呼叫者可略過過去的需求。</span><span class="sxs-lookup"><span data-stu-id="215b8-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="215b8-118">如果您的程式碼會快取安全性資訊，請確定該檢閱的這項弱點。</span><span class="sxs-lookup"><span data-stu-id="215b8-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="215b8-119">完成項中的競爭情形</span><span class="sxs-lookup"><span data-stu-id="215b8-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="215b8-120">物件，參考靜態或不受管理的資源，然後讓其完成項中也可能會發生競爭情形。</span><span class="sxs-lookup"><span data-stu-id="215b8-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="215b8-121">如果多個物件共用資源類別的完成項中操作時，物件必須同步處理所有存取該資源。</span><span class="sxs-lookup"><span data-stu-id="215b8-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="215b8-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="215b8-122">See also</span></span>

- [<span data-ttu-id="215b8-123">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="215b8-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
