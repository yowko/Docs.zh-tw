---
title: "extern (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- extern_CSharpKeyword
- extern
dev_langs:
- CSharp
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
caps.latest.revision: 26
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
ms.openlocfilehash: e499ade5ec8a9339b0d425c59809cf7c177466fb
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="extern-c-reference"></a><span data-ttu-id="52b5f-102">extern (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="52b5f-102">extern (C# Reference)</span></span>
<span data-ttu-id="52b5f-103">`extern` 修飾詞是用來宣告於外部實作的方法。</span><span class="sxs-lookup"><span data-stu-id="52b5f-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="52b5f-104">`extern` 修飾詞的常見用法，是在使用 Interop 服務進行 Unmanaged 程式碼呼叫時，搭配 `DllImport` 屬性使用。</span><span class="sxs-lookup"><span data-stu-id="52b5f-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="52b5f-105">在此情況下，此方法也必須宣告為 `static`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="52b5f-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>  
  
```  
[DllImport("avifil32.dll")]  
private static extern void AVIFileInit();  
```  
  
 <span data-ttu-id="52b5f-106">`extern` 關鍵字也可以定義外部組件別名，這樣就能從單一組件中參考相同元件的不同版本。</span><span class="sxs-lookup"><span data-stu-id="52b5f-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="52b5f-107">如需詳細資訊，請參閱[外部別名](../../../csharp/language-reference/keywords/extern-alias.md)。</span><span class="sxs-lookup"><span data-stu-id="52b5f-107">For more information, see [extern alias](../../../csharp/language-reference/keywords/extern-alias.md).</span></span>  
  
 <span data-ttu-id="52b5f-108">同時使用 [abstract](../../../csharp/language-reference/keywords/abstract.md) 和 `extern` 修飾詞修改同一個成員是錯誤的用法。</span><span class="sxs-lookup"><span data-stu-id="52b5f-108">It is an error to use the [abstract](../../../csharp/language-reference/keywords/abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="52b5f-109">使用 `extern` 修飾詞表示方法是在 C# 程式碼外部實作，而使用 `abstract` 修飾詞則表示類別中並未提供該方法實作。</span><span class="sxs-lookup"><span data-stu-id="52b5f-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>  
  
 <span data-ttu-id="52b5f-110">extern 關鍵字在 C# 中的使用方式比在 C++ 中受到更多限制。</span><span class="sxs-lookup"><span data-stu-id="52b5f-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="52b5f-111">若要比較 C# 關鍵字與 C++ 關鍵字，請參閱＜使用 extern 在 C++ 語言參考中指定連結＞。</span><span class="sxs-lookup"><span data-stu-id="52b5f-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52b5f-112">範例</span><span class="sxs-lookup"><span data-stu-id="52b5f-112">Example</span></span>  
 <span data-ttu-id="52b5f-113">**範例 1**：</span><span class="sxs-lookup"><span data-stu-id="52b5f-113">**Example 1.**</span></span> <span data-ttu-id="52b5f-114">在此範例中，程式會接收來自使用者的字串並且在訊息方塊內顯示該字串。</span><span class="sxs-lookup"><span data-stu-id="52b5f-114">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="52b5f-115">程式會使用從 User32.dll 程式庫匯入的 `MessageBox` 方法。</span><span class="sxs-lookup"><span data-stu-id="52b5f-115">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>  
  
 <span data-ttu-id="52b5f-116">[!code-cs[csrefKeywordsModifiers#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/extern_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="52b5f-116">[!code-cs[csrefKeywordsModifiers#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/extern_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="52b5f-117">範例</span><span class="sxs-lookup"><span data-stu-id="52b5f-117">Example</span></span>  
 <span data-ttu-id="52b5f-118">**範例 2**：</span><span class="sxs-lookup"><span data-stu-id="52b5f-118">**Example 2.**</span></span> <span data-ttu-id="52b5f-119">此範例將示範呼叫 C 程式庫 (原生 DLL) 的 C# 程式。</span><span class="sxs-lookup"><span data-stu-id="52b5f-119">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>  
  
 1. <span data-ttu-id="52b5f-120">請建立下列 C 檔案並將它命名為 `cmdll.c`：</span><span class="sxs-lookup"><span data-stu-id="52b5f-120">Create the following C file and name it `cmdll.c`:</span></span>  
  
```  
// cmdll.c  
// Compile with: /LD  
int __declspec(dllexport) SampleMethod(int i)  
{  
   return i*10;  
}  
```  
  
## <a name="example"></a><span data-ttu-id="52b5f-121">範例</span><span class="sxs-lookup"><span data-stu-id="52b5f-121">Example</span></span>  
 2. <span data-ttu-id="52b5f-122">從 Visual Studio 安裝目錄開啟 Visual Studio x64 (或 x32) Native Tools [命令提示字元] 視窗，並在命令提示字元中鍵入 **cl /LD cmdll.c** 來編譯 `cmdll.c` 檔案。</span><span class="sxs-lookup"><span data-stu-id="52b5f-122">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl /LD cmdll.c** at the command prompt.</span></span>  
  
 3. <span data-ttu-id="52b5f-123">在相同的目錄中，建立下列 C# 檔案並將它命名為 `cm.cs`：</span><span class="sxs-lookup"><span data-stu-id="52b5f-123">In the same directory, create the following C# file and name it `cm.cs`:</span></span>  
  
```  
// cm.cs  
using System;  
using System.Runtime.InteropServices;  
public class MainClass   
{  
   [DllImport("Cmdll.dll")]  
   public static extern int SampleMethod(int x);  
  
   static void Main()   
   {  
      Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="52b5f-124">範例</span><span class="sxs-lookup"><span data-stu-id="52b5f-124">Example</span></span>  
 3. <span data-ttu-id="52b5f-125">從 Visual Studio 安裝目錄開啟 Visual Studio x64 (或 x32) Native Tools [命令提示字元] 視窗，並輸入下列內容來編譯 `cm.cs` 檔案：</span><span class="sxs-lookup"><span data-stu-id="52b5f-125">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>  
  
> <span data-ttu-id="52b5f-126">**csc cm.cs** (適用於 x64 命令提示字元)</span><span class="sxs-lookup"><span data-stu-id="52b5f-126">**csc cm.cs** (for the x64 command prompt)</span></span>   
>  <span data-ttu-id="52b5f-127">-或-</span><span class="sxs-lookup"><span data-stu-id="52b5f-127">—or—</span></span>  
> <span data-ttu-id="52b5f-128">**csc /platform:x86 cm.cs** (適用於 x32 命令提示字元)</span><span class="sxs-lookup"><span data-stu-id="52b5f-128">**csc /platform:x86 cm.cs** (for the x32 command prompt)</span></span>  
  
 <span data-ttu-id="52b5f-129">這樣將會建立可執行檔 `cm.exe`。</span><span class="sxs-lookup"><span data-stu-id="52b5f-129">This will create the executable file `cm.exe`.</span></span>  
  
 4. <span data-ttu-id="52b5f-130">執行 `cm.exe`。</span><span class="sxs-lookup"><span data-stu-id="52b5f-130">Run `cm.exe`.</span></span> <span data-ttu-id="52b5f-131">`SampleMethod` 方法會將值 5 傳遞至 DLL 檔案，並傳回乘以 10 的值。</span><span class="sxs-lookup"><span data-stu-id="52b5f-131">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="52b5f-132">此程式會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="52b5f-132">The program produces the following output:</span></span>  
  
```  
SampleMethod() returns 50.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="52b5f-133">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="52b5f-133">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="52b5f-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52b5f-134">See Also</span></span>  
 <span data-ttu-id="52b5f-135"><xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="52b5f-135"><xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName></span></span>   
 <span data-ttu-id="52b5f-136">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="52b5f-136">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="52b5f-137">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="52b5f-137">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="52b5f-138">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="52b5f-138">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="52b5f-139">修飾詞</span><span class="sxs-lookup"><span data-stu-id="52b5f-139">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)

