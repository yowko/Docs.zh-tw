---
title: -win32res (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: 4026fcbd7dc2ef29c1e7ee01a0f37b3ff471b187
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322370"
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="d5a2a-102">-win32res (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="d5a2a-102">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="d5a2a-103">**-win32res** 選項會將 Win32 資源插入至輸出檔案中。</span><span class="sxs-lookup"><span data-stu-id="d5a2a-103">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5a2a-104">語法</span><span class="sxs-lookup"><span data-stu-id="d5a2a-104">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="d5a2a-105">引數</span><span class="sxs-lookup"><span data-stu-id="d5a2a-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="d5a2a-106">您想要新增至輸出檔的資源檔。</span><span class="sxs-lookup"><span data-stu-id="d5a2a-106">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5a2a-107">備註</span><span class="sxs-lookup"><span data-stu-id="d5a2a-107">Remarks</span></span>  
 <span data-ttu-id="d5a2a-108">您可以使用[資源編譯器](../../language-reference/compiler-options/resource-compiler-option.md)建立 Win32 資源檔。</span><span class="sxs-lookup"><span data-stu-id="d5a2a-108">A Win32 resource file can be created with the [Resource Compiler](../../language-reference/compiler-options/resource-compiler-option.md).</span></span> <span data-ttu-id="d5a2a-109">資源編譯器是在編譯 Visual C++ 程式時叫用，而 .res 檔案則是從 .rc 檔案建立。</span><span class="sxs-lookup"><span data-stu-id="d5a2a-109">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="d5a2a-110">Win32 資源可以包含版本或點陣圖 (圖示) 資訊，這項資訊可以協助您在 [檔案總管] 中識別應用程式。</span><span class="sxs-lookup"><span data-stu-id="d5a2a-110">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="d5a2a-111">如果您未指定 **-win32res**，編譯器會根據組件版本產生版本資訊。</span><span class="sxs-lookup"><span data-stu-id="d5a2a-111">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="d5a2a-112">請參閱 [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (以參考) 或 [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (以附加) .NET Framework 資源檔。</span><span class="sxs-lookup"><span data-stu-id="d5a2a-112">See [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d5a2a-113">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="d5a2a-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="d5a2a-114">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="d5a2a-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="d5a2a-115">按一下 [應用程式] 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="d5a2a-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="d5a2a-116">按一下 [資源檔] 按鈕，然後使用下拉式方塊選擇檔案。</span><span class="sxs-lookup"><span data-stu-id="d5a2a-116">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5a2a-117">範例</span><span class="sxs-lookup"><span data-stu-id="d5a2a-117">Example</span></span>  
 <span data-ttu-id="d5a2a-118">編譯 `in.cs` 並附加 Win32 資源檔 `rf.res`，以產生 `in.exe`：</span><span class="sxs-lookup"><span data-stu-id="d5a2a-118">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5a2a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5a2a-119">See also</span></span>

- [<span data-ttu-id="d5a2a-120">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="d5a2a-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="d5a2a-121">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="d5a2a-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
