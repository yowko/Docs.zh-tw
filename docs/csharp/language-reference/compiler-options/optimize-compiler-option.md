---
description: -optimize (C# 編譯器選項)
title: -optimize (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
ms.openlocfilehash: 1862794e4d823e38ce19780300a0b04f4e57dc44
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193981"
---
# <a name="-optimize-c-compiler-options"></a><span data-ttu-id="826cc-103">-optimize (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="826cc-103">-optimize (C# Compiler Options)</span></span>

<span data-ttu-id="826cc-104">**-optimize** 選項啟用或停用由編譯器執行的最佳化，讓您的輸出檔案變得更小、更快且更有效率。</span><span class="sxs-lookup"><span data-stu-id="826cc-104">The **-optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="826cc-105">語法</span><span class="sxs-lookup"><span data-stu-id="826cc-105">Syntax</span></span>  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="826cc-106">備註</span><span class="sxs-lookup"><span data-stu-id="826cc-106">Remarks</span></span>  

 <span data-ttu-id="826cc-107">**-optimize** 也會告知通用語言執行平台在執行階段進行程式碼最佳化。</span><span class="sxs-lookup"><span data-stu-id="826cc-107">**-optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="826cc-108">根據預設，會停用最佳化。</span><span class="sxs-lookup"><span data-stu-id="826cc-108">By default, optimizations are disabled.</span></span> <span data-ttu-id="826cc-109">指定 **-optimize+** 以啟用最佳化。</span><span class="sxs-lookup"><span data-stu-id="826cc-109">Specify **-optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="826cc-110">建置組件要使用的模組時，使用與那些組件相同的 **-optimize** 設定。</span><span class="sxs-lookup"><span data-stu-id="826cc-110">When building a module to be used by an assembly, use the same **-optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="826cc-111">**-o** 是 **-optimize** 的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="826cc-111">**-o** is the short form of **-optimize**.</span></span>  
  
 <span data-ttu-id="826cc-112">它可以合併 **-optimize** 和 [-debug](./debug-compiler-option.md) 選項。</span><span class="sxs-lookup"><span data-stu-id="826cc-112">It is possible to combine the **-optimize** and [-debug](./debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="826cc-113">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="826cc-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="826cc-114">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="826cc-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="826cc-115">按一下 [建置] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="826cc-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="826cc-116">修改 **最佳化程式碼** 屬性。</span><span class="sxs-lookup"><span data-stu-id="826cc-116">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="826cc-117">如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>。</span><span class="sxs-lookup"><span data-stu-id="826cc-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="826cc-118">範例</span><span class="sxs-lookup"><span data-stu-id="826cc-118">Example</span></span>  

 <span data-ttu-id="826cc-119">編譯 `t2.cs` 並啟用編譯器最佳化：</span><span class="sxs-lookup"><span data-stu-id="826cc-119">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="826cc-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="826cc-120">See also</span></span>

- [<span data-ttu-id="826cc-121">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="826cc-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="826cc-122">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="826cc-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
