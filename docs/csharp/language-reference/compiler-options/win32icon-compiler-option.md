---
title: -win32icon (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: f3df92d8d0b0135eac1a055afafffa0015fecc2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606272"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="372f4-102">-win32icon (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="372f4-102">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="372f4-103">**-win32icon**選項在輸出檔案中插入一個 .ico 檔，這為輸出檔案在檔資源管理器中提供了所需的外觀。</span><span class="sxs-lookup"><span data-stu-id="372f4-103">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="372f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="372f4-104">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="372f4-105">引數</span><span class="sxs-lookup"><span data-stu-id="372f4-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="372f4-106">您想要新增至輸出檔的 .ico 檔案。</span><span class="sxs-lookup"><span data-stu-id="372f4-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="372f4-107">備註</span><span class="sxs-lookup"><span data-stu-id="372f4-107">Remarks</span></span>  
 <span data-ttu-id="372f4-108">.ico 檔案可以使用 [Resource Compiler](/windows/desktop/menurc/resource-compiler) (資源編譯器) 建立。</span><span class="sxs-lookup"><span data-stu-id="372f4-108">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="372f4-109">資源編譯器是在編譯 Visual C++ 程式時叫用，而 .ico 檔案則是從 .rc 檔案建立。</span><span class="sxs-lookup"><span data-stu-id="372f4-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="372f4-110">請參閱[-連結資源](./linkresource-compiler-option.md)（要引用）或[-資源](./resource-compiler-option.md)（附加）.NET 框架資源檔。</span><span class="sxs-lookup"><span data-stu-id="372f4-110">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="372f4-111">請參閱[-win32res](./win32res-compiler-option.md)以導入 .res 檔。</span><span class="sxs-lookup"><span data-stu-id="372f4-111">See [-win32res](./win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="372f4-112">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="372f4-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="372f4-113">開啟專案的 [屬性]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="372f4-113">Open the project's **Properties** pages.</span></span>  
  
2. <span data-ttu-id="372f4-114">按一下 [應用程式]\*\*\*\* 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="372f4-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="372f4-115">修改**應用程式圖示**屬性。</span><span class="sxs-lookup"><span data-stu-id="372f4-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="372f4-116">如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>。</span><span class="sxs-lookup"><span data-stu-id="372f4-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="372f4-117">範例</span><span class="sxs-lookup"><span data-stu-id="372f4-117">Example</span></span>  
 <span data-ttu-id="372f4-118">編譯 `in.cs` 並附加 .ico 檔案 `rf.ico`，以產生 `in.exe`：</span><span class="sxs-lookup"><span data-stu-id="372f4-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="372f4-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="372f4-119">See also</span></span>

- [<span data-ttu-id="372f4-120">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="372f4-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="372f4-121">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="372f4-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
