---
title: "-target:library (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e66e2edd86dc4a1302b23dab07226a5d56cb79b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="targetlibrary-c-compiler-options"></a><span data-ttu-id="e2d8a-102">/target:library (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="e2d8a-102">/target:library (C# Compiler Options)</span></span>
<span data-ttu-id="e2d8a-103">**/target:library** 選項可讓編譯器建立動態連結程式庫 (DLL)，而不是可執行檔 (EXE)。</span><span class="sxs-lookup"><span data-stu-id="e2d8a-103">The **/target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2d8a-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2d8a-104">Syntax</span></span>  
  
```console  
/target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="e2d8a-105">備註</span><span class="sxs-lookup"><span data-stu-id="e2d8a-105">Remarks</span></span>  
 <span data-ttu-id="e2d8a-106">將建立副檔名為 .dll 的 DLL。</span><span class="sxs-lookup"><span data-stu-id="e2d8a-106">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="e2d8a-107">除非特別使用 [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) 選項指定輸出檔名稱，否則輸出檔名稱會採用第一個輸入檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="e2d8a-107">Unless otherwise specified with the [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="e2d8a-108">指定於命令列時，下一個 **/out** 或 **/target:module** 選項之前的所有檔案都是用來建立 .dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="e2d8a-108">When specified at the command line, all files up to the next **/out** or **/target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="e2d8a-109">建置 .dll 檔案時，不需要 [Main](../../../csharp/programming-guide/main-and-command-args/index.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="e2d8a-109">When building a .dll file, a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e2d8a-110">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="e2d8a-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="e2d8a-111">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="e2d8a-111">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="e2d8a-112">按一下 [應用程式] 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="e2d8a-112">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="e2d8a-113">修改 [輸出類型] 屬性。</span><span class="sxs-lookup"><span data-stu-id="e2d8a-113">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="e2d8a-114">如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。</span><span class="sxs-lookup"><span data-stu-id="e2d8a-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2d8a-115">範例</span><span class="sxs-lookup"><span data-stu-id="e2d8a-115">Example</span></span>  
 <span data-ttu-id="e2d8a-116">建立 `in.dll` 以編譯 `in.cs`：</span><span class="sxs-lookup"><span data-stu-id="e2d8a-116">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc /target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2d8a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2d8a-117">See Also</span></span>  
 [<span data-ttu-id="e2d8a-118">/target （C# 編譯器選項）</span><span class="sxs-lookup"><span data-stu-id="e2d8a-118">/target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="e2d8a-119">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="e2d8a-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
