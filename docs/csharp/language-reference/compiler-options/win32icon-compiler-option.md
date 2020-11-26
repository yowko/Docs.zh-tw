---
description: -win32icon (C# 編譯器選項)
title: -win32icon (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: 5b62bbfe28bb5aa82605a88a83cf82eff9278807
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "91168864"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="5e5ff-103">-win32icon (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="5e5ff-103">-win32icon (C# Compiler Options)</span></span>

<span data-ttu-id="5e5ff-104">**-Win32icon** 選項會在輸出檔中插入 .ico 檔案，讓輸出檔在檔案總管中顯示所需的外觀。</span><span class="sxs-lookup"><span data-stu-id="5e5ff-104">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e5ff-105">語法</span><span class="sxs-lookup"><span data-stu-id="5e5ff-105">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="5e5ff-106">引數</span><span class="sxs-lookup"><span data-stu-id="5e5ff-106">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="5e5ff-107">您想要新增至輸出檔的 .ico 檔案。</span><span class="sxs-lookup"><span data-stu-id="5e5ff-107">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e5ff-108">備註</span><span class="sxs-lookup"><span data-stu-id="5e5ff-108">Remarks</span></span>  

 <span data-ttu-id="5e5ff-109">.ico 檔案可以使用 [Resource Compiler](/windows/desktop/menurc/resource-compiler) (資源編譯器) 建立。</span><span class="sxs-lookup"><span data-stu-id="5e5ff-109">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="5e5ff-110">資源編譯器是在編譯 Visual C++ 程式時叫用，而 .ico 檔案則是從 .rc 檔案建立。</span><span class="sxs-lookup"><span data-stu-id="5e5ff-110">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="5e5ff-111">請參閱 [-linkresource](./linkresource-compiler-option.md) (參考) 或 [資源](./resource-compiler-option.md) (以連結) .NET Framework 資源檔。</span><span class="sxs-lookup"><span data-stu-id="5e5ff-111">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="5e5ff-112">請參閱 [-win32res](./win32res-compiler-option.md) 以匯入 .res 檔案。</span><span class="sxs-lookup"><span data-stu-id="5e5ff-112">See [-win32res](./win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5e5ff-113">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="5e5ff-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="5e5ff-114">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="5e5ff-114">Open the project's **Properties** pages.</span></span>  
  
2. <span data-ttu-id="5e5ff-115">按一下 [應用程式] 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="5e5ff-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="5e5ff-116">修改 **應用程式圖示** 屬性。</span><span class="sxs-lookup"><span data-stu-id="5e5ff-116">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="5e5ff-117">如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>。</span><span class="sxs-lookup"><span data-stu-id="5e5ff-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e5ff-118">範例</span><span class="sxs-lookup"><span data-stu-id="5e5ff-118">Example</span></span>  

 <span data-ttu-id="5e5ff-119">編譯 `in.cs` 並附加 .ico 檔案 `rf.ico`，以產生 `in.exe`：</span><span class="sxs-lookup"><span data-stu-id="5e5ff-119">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e5ff-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e5ff-120">See also</span></span>

- [<span data-ttu-id="5e5ff-121">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="5e5ff-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="5e5ff-122">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="5e5ff-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
