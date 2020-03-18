---
title: -target:library (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: c947b2015c19d0809cab4535e989ee83ebf17fd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606388"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="c3201-102">-target:library (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="c3201-102">-target:library (C# Compiler Options)</span></span>
<span data-ttu-id="c3201-103">**-目標：庫**選項使編譯器創建動態連結程式庫 （DLL）， 而不是可執行檔 （EXE）。</span><span class="sxs-lookup"><span data-stu-id="c3201-103">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3201-104">語法</span><span class="sxs-lookup"><span data-stu-id="c3201-104">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="c3201-105">備註</span><span class="sxs-lookup"><span data-stu-id="c3201-105">Remarks</span></span>  
 <span data-ttu-id="c3201-106">將建立副檔名為 .dll 的 DLL。</span><span class="sxs-lookup"><span data-stu-id="c3201-106">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="c3201-107">除非使用[-out](./out-compiler-option.md)選項另行指定，否則輸出檔案名將採用第一個輸入檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="c3201-107">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="c3201-108">在命令列指定時，所有檔都用於創建 .DLL 檔案，以創建下一**個-出出**或 **-目標：模組**選項。</span><span class="sxs-lookup"><span data-stu-id="c3201-108">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="c3201-109">建置 .dll 檔案時，不需要 [Main](../../programming-guide/main-and-command-args/index.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="c3201-109">When building a .dll file, a [Main](../../programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c3201-110">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="c3201-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="c3201-111">開啟專案的 [屬性]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="c3201-111">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="c3201-112">按一下 [應用程式]\*\*\*\* 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="c3201-112">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="c3201-113">修改 [輸出類型]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="c3201-113">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="c3201-114">如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。</span><span class="sxs-lookup"><span data-stu-id="c3201-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3201-115">範例</span><span class="sxs-lookup"><span data-stu-id="c3201-115">Example</span></span>  
 <span data-ttu-id="c3201-116">建立 `in.dll` 以編譯 `in.cs`：</span><span class="sxs-lookup"><span data-stu-id="c3201-116">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3201-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3201-117">See also</span></span>

- [<span data-ttu-id="c3201-118">-目標（C# 編譯器選項）</span><span class="sxs-lookup"><span data-stu-id="c3201-118">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="c3201-119">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="c3201-119">C# Compiler Options</span></span>](./index.md)
