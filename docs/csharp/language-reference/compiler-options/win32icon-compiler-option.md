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
ms.openlocfilehash: 5014b1da714f8e29f869d4641da93796a607aa4d
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48027782"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="cc2ce-102">-win32icon (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="cc2ce-102">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="cc2ce-103">**-win32icon** 選項會在輸出檔案內插入一個 .ico 檔，讓輸出檔案在檔案總管中具有所需的外觀。</span><span class="sxs-lookup"><span data-stu-id="cc2ce-103">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc2ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="cc2ce-104">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="cc2ce-105">引數</span><span class="sxs-lookup"><span data-stu-id="cc2ce-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="cc2ce-106">您想要新增至輸出檔的 .ico 檔案。</span><span class="sxs-lookup"><span data-stu-id="cc2ce-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc2ce-107">備註</span><span class="sxs-lookup"><span data-stu-id="cc2ce-107">Remarks</span></span>  
 <span data-ttu-id="cc2ce-108">.ico 檔案可以使用 [Resource Compiler](/windows/desktop/menurc/resource-compiler) (資源編譯器) 建立。</span><span class="sxs-lookup"><span data-stu-id="cc2ce-108">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="cc2ce-109">資源編譯器是在編譯 Visual C++ 程式時叫用，而 .ico 檔案則是從 .rc 檔案建立。</span><span class="sxs-lookup"><span data-stu-id="cc2ce-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="cc2ce-110">請參閱 [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (以參考) 或 [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (以附加) .NET Framework 資源檔。</span><span class="sxs-lookup"><span data-stu-id="cc2ce-110">See [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="cc2ce-111">請參閱 [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) 以匯入 .res 檔案。</span><span class="sxs-lookup"><span data-stu-id="cc2ce-111">See [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="cc2ce-112">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="cc2ce-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="cc2ce-113">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="cc2ce-113">Open the project's **Properties** pages.</span></span>  
  
2.  <span data-ttu-id="cc2ce-114">按一下 [應用程式] 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="cc2ce-114">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="cc2ce-115">修改**應用程式圖示**屬性。</span><span class="sxs-lookup"><span data-stu-id="cc2ce-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="cc2ce-116">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>。</span><span class="sxs-lookup"><span data-stu-id="cc2ce-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc2ce-117">範例</span><span class="sxs-lookup"><span data-stu-id="cc2ce-117">Example</span></span>  
 <span data-ttu-id="cc2ce-118">編譯 `in.cs` 並附加 .ico 檔案 `rf.ico`，以產生 `in.exe`：</span><span class="sxs-lookup"><span data-stu-id="cc2ce-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc2ce-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="cc2ce-119">See Also</span></span>  

- [<span data-ttu-id="cc2ce-120">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="cc2ce-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="cc2ce-121">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="cc2ce-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
