---
description: -target:library (C# 編譯器選項)
title: -target:library (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: 953249c4d0168ed3d279d03a0b2fb63d8ff6d5f5
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128474"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="1758b-103">-target:library (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="1758b-103">-target:library (C# Compiler Options)</span></span>
<span data-ttu-id="1758b-104">**-Target： library**選項會讓編譯器建立動態連結程式庫 (DLL) ，而不是 (EXE) 的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="1758b-104">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1758b-105">語法</span><span class="sxs-lookup"><span data-stu-id="1758b-105">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="1758b-106">備註</span><span class="sxs-lookup"><span data-stu-id="1758b-106">Remarks</span></span>  
 <span data-ttu-id="1758b-107">將建立副檔名為 .dll 的 DLL。</span><span class="sxs-lookup"><span data-stu-id="1758b-107">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="1758b-108">除非另行指定，否則[-out](./out-compiler-option.md)輸出檔名稱會採用第一個輸入檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="1758b-108">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="1758b-109">當您在命令列指定時，會使用下一個或 **-target： module**選項**之前的所有**檔案來建立 .dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="1758b-109">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="1758b-110">建置 .dll 檔案時，不需要 [Main](../../programming-guide/main-and-command-args/index.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="1758b-110">When building a .dll file, a [Main](../../programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1758b-111">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="1758b-111">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="1758b-112">開啟專案的 [屬性]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="1758b-112">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="1758b-113">按一下 [應用程式]\*\*\*\* 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="1758b-113">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="1758b-114">修改 [輸出類型]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="1758b-114">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="1758b-115">如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。</span><span class="sxs-lookup"><span data-stu-id="1758b-115">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1758b-116">範例</span><span class="sxs-lookup"><span data-stu-id="1758b-116">Example</span></span>  
 <span data-ttu-id="1758b-117">建立 `in.dll` 以編譯 `in.cs`：</span><span class="sxs-lookup"><span data-stu-id="1758b-117">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="1758b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1758b-118">See also</span></span>

- [<span data-ttu-id="1758b-119">-目標 (c # 編譯器選項) </span><span class="sxs-lookup"><span data-stu-id="1758b-119">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="1758b-120">C # 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="1758b-120">C# Compiler Options</span></span>](./index.md)
