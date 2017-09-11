---
title: "如何：攔截非 CLS 例外狀況"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
caps.latest.revision: 8
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 18a19fe34b8ec13bd9fc6d25335d0931a22ce4a3
ms.contentlocale: zh-tw
ms.lasthandoff: 09/08/2017

---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="3e132-102">如何：攔截非 CLS 例外狀況</span><span class="sxs-lookup"><span data-stu-id="3e132-102">How to: Catch a non-CLS Exception</span></span>
<span data-ttu-id="3e132-103">包括 C++/CLI 在內的某些 .NET 語言，允許物件擲回非衍生自 <xref:System.Exception> 的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3e132-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="3e132-104">這類例外狀況稱之為「非 CLS 例外狀況」或「非例外狀況」。</span><span class="sxs-lookup"><span data-stu-id="3e132-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="3e132-105">在 [!INCLUDE[csprcs](~/includes/csprcs-md.md)] 中無法擲回非 CLS 例外狀況，但有兩種方式可以攔截它們︰</span><span class="sxs-lookup"><span data-stu-id="3e132-105">In [!INCLUDE[csprcs](~/includes/csprcs-md.md)] you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
-   <span data-ttu-id="3e132-106">在 `catch (Exception e)` 區塊內為 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>。</span><span class="sxs-lookup"><span data-stu-id="3e132-106">Within a `catch (Exception e)` block as a <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span></span>  
  
     <span data-ttu-id="3e132-107">根據預設，[!INCLUDE[csprcs](~/includes/csprcs-md.md)] 組件會將非 CLS 例外狀況當成包裝例外狀況攔截。</span><span class="sxs-lookup"><span data-stu-id="3e132-107">By default, a [!INCLUDE[csprcs](~/includes/csprcs-md.md)] assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="3e132-108">如果您需要存取原始的例外狀況 (它可以透過 <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> 屬性存取)，請使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="3e132-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property.</span></span> <span data-ttu-id="3e132-109">本主題稍後的程序會說明如何以這種方式攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3e132-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
-   <span data-ttu-id="3e132-110">在一般的 catch 區塊 (不指定例外狀況類型的 catch 區塊) 內，它會放在 `catch (Exception)` 或 `catch (Exception e)` 區塊的後面。</span><span class="sxs-lookup"><span data-stu-id="3e132-110">Within a general catch block (a catch block without an exception type specified) that is put after a `catch (Exception)` or `catch (Exception e)` block.</span></span>  
  
     <span data-ttu-id="3e132-111">當您想要執行某些動作 (例如寫入記錄檔) 以回應非 CLS 例外狀況時，請使用這個方法，您不需要存取例外狀況資訊。</span><span class="sxs-lookup"><span data-stu-id="3e132-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="3e132-112">Common Language Runtime 預設會包裝所有的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3e132-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="3e132-113">若要停用此行為，請將此組件層級屬性新增至程式碼，通常在 AssemblyInfo.cs 檔案中︰`[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`。</span><span class="sxs-lookup"><span data-stu-id="3e132-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="3e132-114">攔截非 CLS 例外狀況</span><span class="sxs-lookup"><span data-stu-id="3e132-114">To catch a non-CLS exception</span></span>  
  
1.  <span data-ttu-id="3e132-115">在 `catch(Exception e) block` 內，使用 `as` 關鍵字測試 `e` 是否可轉換成 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>。</span><span class="sxs-lookup"><span data-stu-id="3e132-115">Within a `catch(Exception e) block`, use the `as` keyword to test whether `e` can be cast to a <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span></span>  
  
2.  <span data-ttu-id="3e132-116">透過 <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> 屬性存取原始的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3e132-116">Access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e132-117">範例</span><span class="sxs-lookup"><span data-stu-id="3e132-117">Example</span></span>  
 <span data-ttu-id="3e132-118">下例示範如何攔截從以 C++/CLR 撰寫的類別庫擲回的非 CLS 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3e132-118">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLR.</span></span> <span data-ttu-id="3e132-119">請注意，本例的 [!INCLUDE[csprcs](~/includes/csprcs-md.md)] 用戶端程式碼點事先知道被擲回的例外狀況類型是 <xref:System.String?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="3e132-119">Note that in this example, the [!INCLUDE[csprcs](~/includes/csprcs-md.md)] client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=fullName>.</span></span> <span data-ttu-id="3e132-120">您可以將 <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> 屬性轉換回原始類型，只要您可從程式碼存取該類型。</span><span class="sxs-lookup"><span data-stu-id="3e132-120">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property back its original type as long as that type is accessible from your code.</span></span>  
  
```  
// Class library written in C++/CLR.  
   ThrowNonCLS.Class1 myClass = new ThrowNonCLS.Class1();  
  
   try  
   {  
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();   
   }  
  
   catch (Exception e)  
   {  
    RuntimeWrappedException rwe = e as RuntimeWrappedException;  
    if (rwe != null)      
    {  
      String s = rwe.WrappedException as String;  
      if (s != null)  
      {  
        Console.WriteLine(s);  
      }  
    }  
    else  
    {  
       // Handle other System.Exception types.  
    }  
   }             
```  
  
## <a name="see-also"></a><span data-ttu-id="3e132-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e132-121">See Also</span></span>  
 <span data-ttu-id="3e132-122"><xref:System.Runtime.CompilerServices.RuntimeWrappedException></span><span class="sxs-lookup"><span data-stu-id="3e132-122"><xref:System.Runtime.CompilerServices.RuntimeWrappedException></span></span>   
 [<span data-ttu-id="3e132-123">例外狀況和例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="3e132-123">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)

