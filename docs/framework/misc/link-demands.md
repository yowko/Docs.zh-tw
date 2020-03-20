---
title: 連結要求
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
ms.openlocfilehash: a0466eb5c24840c77a3b191f9b0e001f6b267fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181165"
---
# <a name="link-demands"></a><span data-ttu-id="707c9-102">連結要求</span><span class="sxs-lookup"><span data-stu-id="707c9-102">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="707c9-103">連結要求會在 Just-In-Time 編譯期間進行安全性檢查，並且只檢查程式碼組件的即時呼叫者。</span><span class="sxs-lookup"><span data-stu-id="707c9-103">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="707c9-104">當您的程式碼繫結至類型參考，包括函式指標參考和方法呼叫時，連結就會發生。</span><span class="sxs-lookup"><span data-stu-id="707c9-104">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="707c9-105">如果呼叫的組件並沒有足夠權限可連結到您的程式碼，則程式碼載入和執行時不會允許連結且會擲回執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="707c9-105">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="707c9-106">連結要求可以在繼承自您的程式碼的類別中被覆寫。</span><span class="sxs-lookup"><span data-stu-id="707c9-106">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="707c9-107">請注意，對這種類型的需求不會執行完整堆疊查核行程，而且您的程式碼仍會受到引誘攻擊。</span><span class="sxs-lookup"><span data-stu-id="707c9-107">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="707c9-108">例如，如果程式集 A 中的方法受鏈路請求保護，則根據程式集 B 的許可權計算程式集 B 中的直接調用方。 但是，如果鏈路要求在裝配體 B 中使用方法間接調用程式集 A 中的方法，則不會計算程式集 C 中的方法。連結請求僅指定直接調用程式集中必須連結到代碼的許可權。</span><span class="sxs-lookup"><span data-stu-id="707c9-108">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="707c9-109">它並未指定所有呼叫端必須擁有以便執行程式碼的權限。</span><span class="sxs-lookup"><span data-stu-id="707c9-109">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="707c9-110"><xref:System.Security.CodeAccessPermission.Assert%2A>、<xref:System.Security.CodeAccessPermission.Deny%2A> 和 <xref:System.Security.CodeAccessPermission.PermitOnly%2A> 堆疊查核行程修飾詞不會影響連結要求的評估。</span><span class="sxs-lookup"><span data-stu-id="707c9-110">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="707c9-111">由於連結要求不會執行堆疊查核行程，堆疊查核行程修飾詞不會影響連結要求。</span><span class="sxs-lookup"><span data-stu-id="707c9-111">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="707c9-112">如果通過[反射](../reflection-and-codedom/reflection.md)訪問受連結請求保護的方法，則連結請求將檢查通過反射訪問的代碼的直接調用方。</span><span class="sxs-lookup"><span data-stu-id="707c9-112">If a method protected by a link demand is accessed through [Reflection](../reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="707c9-113">使用反映來執行的方法探索和方法引動過程都是如此。</span><span class="sxs-lookup"><span data-stu-id="707c9-113">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="707c9-114">例如，假設代碼使用反射返回表示受連結<xref:System.Reflection.MethodInfo>請求保護的方法的物件，然後將**該方法資訊**物件傳遞給使用該物件調用原始方法的其他代碼。</span><span class="sxs-lookup"><span data-stu-id="707c9-114">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="707c9-115">在這種情況下，連結需求檢查發生兩次：一次用於返回**MethodInfo**物件的代碼，一次用於調用它的代碼。</span><span class="sxs-lookup"><span data-stu-id="707c9-115">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="707c9-116">在靜態類別建構函式上執行的連結要求不會保護建構函式，因為靜態建構函式由系統所呼叫，不在應用程式的程式碼執行路徑中。</span><span class="sxs-lookup"><span data-stu-id="707c9-116">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="707c9-117">如此一來，當連結需求套用至整個類別時，它無法保護對靜態建構函式的存取權，不過它確實會保護類別的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="707c9-117">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="707c9-118">下列程式碼片段以宣告方式指定連結至 `ReadData` 方法的任何程式碼都必須具有 `CustomPermission` 權限。</span><span class="sxs-lookup"><span data-stu-id="707c9-118">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="707c9-119">此權限是假設的自訂權限，並不存在於 .NET Framework 中。</span><span class="sxs-lookup"><span data-stu-id="707c9-119">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="707c9-120">通過將**安全操作.LinkDemand**標誌傳遞給 。 `CustomPermissionAttribute`</span><span class="sxs-lookup"><span data-stu-id="707c9-120">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
```vb  
<CustomPermissionAttribute(SecurityAction.LinkDemand)> _  
Public Shared Function ReadData() As String  
    ' Access a custom resource.  
End Function
```  
  
```csharp  
[CustomPermissionAttribute(SecurityAction.LinkDemand)]  
public static string ReadData()  
{  
    // Access a custom resource.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="707c9-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="707c9-121">See also</span></span>

- [<span data-ttu-id="707c9-122">屬性</span><span class="sxs-lookup"><span data-stu-id="707c9-122">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="707c9-123">代碼訪問安全性</span><span class="sxs-lookup"><span data-stu-id="707c9-123">Code Access Security</span></span>](code-access-security.md)
