---
title: -pathmap (C# 編譯器選項)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 277ab8e094f28fd5e3cbba4de12e742bb9614730
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47425780"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="7856c-102">-pathmap (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="7856c-102">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="7856c-103">**-pathmap** 編譯器選項會指定如何將實體路徑對應到編譯器所輸出的來源路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="7856c-103">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="7856c-104">語法</span><span class="sxs-lookup"><span data-stu-id="7856c-104">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="7856c-105">引數</span><span class="sxs-lookup"><span data-stu-id="7856c-105">Arguments</span></span>

 <span data-ttu-id="7856c-106">`path1` 目前環境中原始程式檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="7856c-106">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="7856c-107">`sourcePath1` 任何輸出檔案中替代 `path1` 的來源路徑。</span><span class="sxs-lookup"><span data-stu-id="7856c-107">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="7856c-108">若要指定多個對應的來源路徑，請以逗號隔開每個來源路徑。</span><span class="sxs-lookup"><span data-stu-id="7856c-108">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="7856c-109">備註</span><span class="sxs-lookup"><span data-stu-id="7856c-109">Remarks</span></span>

<span data-ttu-id="7856c-110">編譯器會基於下列因素，將來源路徑寫入其輸出中：</span><span class="sxs-lookup"><span data-stu-id="7856c-110">The compiler writes the source path path into its output for the following reasons:</span></span>

1. <span data-ttu-id="7856c-111">將 <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> 套用到選擇性參數時，會針對引數替代來源路徑。</span><span class="sxs-lookup"><span data-stu-id="7856c-111">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="7856c-112">來源路徑內嵌於 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="7856c-112">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="7856c-113">PDB 檔案的路徑內嵌於 PE (可攜式執行檔) 檔案。</span><span class="sxs-lookup"><span data-stu-id="7856c-113">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="7856c-114">此選項會將編譯器執行所在電腦上的每個實體路徑對應到應寫入輸出檔案的對應路徑。</span><span class="sxs-lookup"><span data-stu-id="7856c-114">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="7856c-115">範例</span><span class="sxs-lookup"><span data-stu-id="7856c-115">Example</span></span>

<span data-ttu-id="7856c-116">在目錄 **C:\\work\\tests** 中編譯 `t.cs`，並將該目錄對應到輸出中的 **\publish**：</span><span class="sxs-lookup"><span data-stu-id="7856c-116">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="7856c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7856c-117">See also</span></span>

- [<span data-ttu-id="7856c-118">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="7856c-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="7856c-119">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="7856c-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
