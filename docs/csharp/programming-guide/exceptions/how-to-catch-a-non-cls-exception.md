---
title: 如何攔截非 CLS 例外狀況
description: 瞭解如何攔截非 CLS 例外狀況。 請參閱程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: db723cb1e29181e9462c5b423c66cdf8de659259
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178667"
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="b8f0a-104">如何攔截非 CLS 例外狀況</span><span class="sxs-lookup"><span data-stu-id="b8f0a-104">How to catch a non-CLS exception</span></span>

<span data-ttu-id="b8f0a-105">包括 C++/CLI 在內的某些 .NET 語言，允許物件擲回非衍生自 <xref:System.Exception> 的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b8f0a-105">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="b8f0a-106">這類例外狀況稱之為「非 CLS 例外狀況」\*\* 或「非例外狀況」\*\*。</span><span class="sxs-lookup"><span data-stu-id="b8f0a-106">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="b8f0a-107">在 C# 中無法擲回非 CLS 例外狀況，但有兩種方式可以攔截它們︰</span><span class="sxs-lookup"><span data-stu-id="b8f0a-107">In C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
- <span data-ttu-id="b8f0a-108">在 `catch (RuntimeWrappedException e)` 區塊內。</span><span class="sxs-lookup"><span data-stu-id="b8f0a-108">Within a `catch (RuntimeWrappedException e)` block.</span></span>
  
     <span data-ttu-id="b8f0a-109">根據預設，Visual C# 組件會將非 CLS 例外狀況當成包裝例外狀況攔截。</span><span class="sxs-lookup"><span data-stu-id="b8f0a-109">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="b8f0a-110">如果您需要存取原始的例外狀況 (它可以透過 <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> 屬性存取)，請使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="b8f0a-110">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b8f0a-111">本主題稍後的程序會說明如何以這種方式攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b8f0a-111">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
- <span data-ttu-id="b8f0a-112">在一般的 catch 區塊 (不指定例外狀況類型的 catch 區塊) 內，它會放在所有其他 `catch` 區塊的後面。</span><span class="sxs-lookup"><span data-stu-id="b8f0a-112">Within a general catch block (a catch block without an exception type specified) that is put after all other `catch` blocks.</span></span>
  
     <span data-ttu-id="b8f0a-113">當您想要執行某些動作 (例如寫入記錄檔) 以回應非 CLS 例外狀況時，請使用這個方法，您不需要存取例外狀況資訊。</span><span class="sxs-lookup"><span data-stu-id="b8f0a-113">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="b8f0a-114">Common Language Runtime 預設會包裝所有的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b8f0a-114">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="b8f0a-115">若要停用此行為，請將此組件層級屬性新增至程式碼，通常在 AssemblyInfo.cs 檔案中︰`[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`。</span><span class="sxs-lookup"><span data-stu-id="b8f0a-115">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="b8f0a-116">攔截非 CLS 例外狀況</span><span class="sxs-lookup"><span data-stu-id="b8f0a-116">To catch a non-CLS exception</span></span>  
  
<span data-ttu-id="b8f0a-117">在 `catch(RuntimeWrappedException e)` 區塊內，透過 <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> 屬性存取原始的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b8f0a-117">Within a `catch(RuntimeWrappedException e)` block, access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8f0a-118">範例</span><span class="sxs-lookup"><span data-stu-id="b8f0a-118">Example</span></span>  

 <span data-ttu-id="b8f0a-119">下例示範如何攔截從以 C++/CLI 撰寫的類別庫擲回的非 CLS 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b8f0a-119">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLI.</span></span> <span data-ttu-id="b8f0a-120">請注意，本例的 C# 用戶端程式碼事先知道被擲回的例外狀況類型是 <xref:System.String?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b8f0a-120">Note that in this example, the C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b8f0a-121">您可以將 <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> 屬性轉換回原始類型，只要您可從程式碼存取該類型。</span><span class="sxs-lookup"><span data-stu-id="b8f0a-121">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property back its original type as long as that type is accessible from your code.</span></span>  
  
```csharp
// Class library written in C++/CLI.
var myClass = new ThrowNonCLS.Class1();

try
{
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();
}
catch (RuntimeWrappedException e)
{
    String s = e.WrappedException as String;
    if (s != null)
    {
        Console.WriteLine(s);
    }
}
```  
  
## <a name="see-also"></a><span data-ttu-id="b8f0a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8f0a-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [<span data-ttu-id="b8f0a-123">例外狀況和例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="b8f0a-123">Exceptions and Exception Handling</span></span>](./index.md)
