---
title: extern 修飾詞 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: aca1a9fa0b57e9b3b0a515a805039ade2fe0c2f1
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027911"
---
# <a name="extern-c-reference"></a><span data-ttu-id="3ae18-102">extern (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3ae18-102">extern (C# Reference)</span></span>

<span data-ttu-id="3ae18-103">`extern` 修飾詞是用來宣告於外部實作的方法。</span><span class="sxs-lookup"><span data-stu-id="3ae18-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="3ae18-104">`extern` 修飾詞的常見用法，是在使用 Interop 服務進行 Unmanaged 程式碼呼叫時，搭配 `DllImport` 屬性使用。</span><span class="sxs-lookup"><span data-stu-id="3ae18-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="3ae18-105">在此情況下，此方法也必須宣告為 `static`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="3ae18-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="3ae18-106">`extern` 關鍵字也可以定義外部組件別名，這樣就能從單一組件中參考相同元件的不同版本。</span><span class="sxs-lookup"><span data-stu-id="3ae18-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="3ae18-107">如需詳細資訊，請參閱[外部別名](extern-alias.md)。</span><span class="sxs-lookup"><span data-stu-id="3ae18-107">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="3ae18-108">同時使用 [abstract](abstract.md) 和 `extern` 修飾詞修改同一個成員是錯誤的用法。</span><span class="sxs-lookup"><span data-stu-id="3ae18-108">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="3ae18-109">使用 `extern` 修飾詞表示方法是在 C# 程式碼外部實作，而使用 `abstract` 修飾詞則表示類別中並未提供該方法實作。</span><span class="sxs-lookup"><span data-stu-id="3ae18-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="3ae18-110">extern 關鍵字在 C# 中的使用方式比在 C++ 中受到更多限制。</span><span class="sxs-lookup"><span data-stu-id="3ae18-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="3ae18-111">若要比較 C# 關鍵字與 C++ 關鍵字，請參閱＜使用 extern 在 C++ 語言參考中指定連結＞。</span><span class="sxs-lookup"><span data-stu-id="3ae18-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="3ae18-112">範例 1</span><span class="sxs-lookup"><span data-stu-id="3ae18-112">Example 1</span></span>

<span data-ttu-id="3ae18-113">在此範例中，程式會接收來自使用者的字串並且在訊息方塊內顯示該字串。</span><span class="sxs-lookup"><span data-stu-id="3ae18-113">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="3ae18-114">程式會使用從 User32.dll 程式庫匯入的 `MessageBox` 方法。</span><span class="sxs-lookup"><span data-stu-id="3ae18-114">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="3ae18-115">範例 2</span><span class="sxs-lookup"><span data-stu-id="3ae18-115">Example 2</span></span>

<span data-ttu-id="3ae18-116">此範例將示範呼叫 C 程式庫 (原生 DLL) 的 C# 程式。</span><span class="sxs-lookup"><span data-stu-id="3ae18-116">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="3ae18-117">請建立下列 C 檔案並將它命名為 `cmdll.c`：</span><span class="sxs-lookup"><span data-stu-id="3ae18-117">Create the following C file and name it `cmdll.c`:</span></span>

```c
// cmdll.c
// Compile with: -LD
int __declspec(dllexport) SampleMethod(int i)
{
  return i*10;
}
```

2. <span data-ttu-id="3ae18-118">從 Visual Studio 安裝目錄開啟 Visual Studio x64 (或 x32) Native Tools [命令提示字元] 視窗，並在命令提示字元中鍵入 **cl -LD cmdll.c** 來編譯 `cmdll.c` 檔案。</span><span class="sxs-lookup"><span data-stu-id="3ae18-118">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="3ae18-119">在相同的目錄中，建立下列 C# 檔案並將它命名為 `cm.cs`：</span><span class="sxs-lookup"><span data-stu-id="3ae18-119">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

```csharp
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

4. <span data-ttu-id="3ae18-120">從 Visual Studio 安裝目錄開啟 Visual Studio x64 (或 x32) Native Tools [命令提示字元] 視窗，並輸入下列內容來編譯 `cm.cs` 檔案：</span><span class="sxs-lookup"><span data-stu-id="3ae18-120">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

> <span data-ttu-id="3ae18-121">**csc cm.cs** (適用於 x64 命令提示字元) - 或 - **csc -platform:x86 cm.cs** (適用於 x32 命令提示字元)</span><span class="sxs-lookup"><span data-stu-id="3ae18-121">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

<span data-ttu-id="3ae18-122">這樣將會建立可執行檔 `cm.exe`。</span><span class="sxs-lookup"><span data-stu-id="3ae18-122">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="3ae18-123">執行 `cm.exe`。</span><span class="sxs-lookup"><span data-stu-id="3ae18-123">Run `cm.exe`.</span></span> <span data-ttu-id="3ae18-124">`SampleMethod` 方法會將值 5 傳遞至 DLL 檔案，並傳回乘以 10 的值。</span><span class="sxs-lookup"><span data-stu-id="3ae18-124">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="3ae18-125">此程式會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="3ae18-125">The program produces the following output:</span></span>

```
SampleMethod() returns 50.
```

## <a name="c-language-specification"></a><span data-ttu-id="3ae18-126">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="3ae18-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3ae18-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ae18-127">See also</span></span>

<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>  
[<span data-ttu-id="3ae18-128">C# 參考</span><span class="sxs-lookup"><span data-stu-id="3ae18-128">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="3ae18-129">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3ae18-129">C# Programming Guide</span></span>](../../programming-guide/index.md)  
[<span data-ttu-id="3ae18-130">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="3ae18-130">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="3ae18-131">修飾詞</span><span class="sxs-lookup"><span data-stu-id="3ae18-131">Modifiers</span></span>](modifiers.md)  