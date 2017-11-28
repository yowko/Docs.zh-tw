---
title: "-optimize (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d74a338336d5878cb8d6f212076bb9f1eb7ef768
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="optimize-c-compiler-options"></a><span data-ttu-id="d491a-102">/optimize (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="d491a-102">/optimize (C# Compiler Options)</span></span>
<span data-ttu-id="d491a-103">**/optimize** 選項啟用或停用由編譯器執行的最佳化，讓您的輸出檔變得更小、更快且更有效率。</span><span class="sxs-lookup"><span data-stu-id="d491a-103">The **/optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d491a-104">語法</span><span class="sxs-lookup"><span data-stu-id="d491a-104">Syntax</span></span>  
  
```console  
/optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="d491a-105">備註</span><span class="sxs-lookup"><span data-stu-id="d491a-105">Remarks</span></span>  
 <span data-ttu-id="d491a-106">**/optimize** 也會告知 Common Language Runtime 在執行階段進行程式碼最佳化。</span><span class="sxs-lookup"><span data-stu-id="d491a-106">**/optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="d491a-107">根據預設，會停用最佳化。</span><span class="sxs-lookup"><span data-stu-id="d491a-107">By default, optimizations are disabled.</span></span> <span data-ttu-id="d491a-108">指定 **/optimize+** 以啟用最佳化。</span><span class="sxs-lookup"><span data-stu-id="d491a-108">Specify **/optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="d491a-109">建置組件要使用的模組時，使用與那些組件相同的 **/optimize** 設定。</span><span class="sxs-lookup"><span data-stu-id="d491a-109">When building a module to be used by an assembly, use the same **/optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="d491a-110">**/o** 是 **/optimize** 的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="d491a-110">**/o** is the short form of **/optimize**.</span></span>  
  
 <span data-ttu-id="d491a-111">它可以合併 **/optimize** 和 [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) 選項。</span><span class="sxs-lookup"><span data-stu-id="d491a-111">It is possible to combine the **/optimize** and [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d491a-112">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="d491a-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="d491a-113">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="d491a-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="d491a-114">按一下 [建置] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="d491a-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="d491a-115">修改**最佳化程式碼**屬性。</span><span class="sxs-lookup"><span data-stu-id="d491a-115">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="d491a-116">如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>。</span><span class="sxs-lookup"><span data-stu-id="d491a-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d491a-117">範例</span><span class="sxs-lookup"><span data-stu-id="d491a-117">Example</span></span>  
 <span data-ttu-id="d491a-118">編譯 `t2.cs` 並啟用編譯器最佳化：</span><span class="sxs-lookup"><span data-stu-id="d491a-118">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs /optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="d491a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d491a-119">See Also</span></span>  
 [<span data-ttu-id="d491a-120">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="d491a-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="d491a-121">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="d491a-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
