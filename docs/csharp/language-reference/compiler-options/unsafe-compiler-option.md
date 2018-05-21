---
title: -unsafe (C# 編譯器選項)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: e308cae4a46efd53a77baf5b175e9069b5371fa4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="cfc4e-102">-unsafe (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="cfc4e-102">-unsafe (C# Compiler Options)</span></span>
<span data-ttu-id="cfc4e-103">**-unsafe** 編譯器選項允許程式碼使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 關鍵字來進行編譯。</span><span class="sxs-lookup"><span data-stu-id="cfc4e-103">The **-unsafe** compiler option allows code that uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfc4e-104">語法</span><span class="sxs-lookup"><span data-stu-id="cfc4e-104">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="cfc4e-105">備註</span><span class="sxs-lookup"><span data-stu-id="cfc4e-105">Remarks</span></span>  
 <span data-ttu-id="cfc4e-106">如需 Unsafe 程式碼的詳細資訊，請參閱 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="cfc4e-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="cfc4e-107">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="cfc4e-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="cfc4e-108">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="cfc4e-108">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="cfc4e-109">按一下 [建置] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="cfc4e-109">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="cfc4e-110">選取 [容許 Unsafe 程式碼] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="cfc4e-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="cfc4e-111">在 csproj 檔案中新增此選項</span><span class="sxs-lookup"><span data-stu-id="cfc4e-111">To add this option in a csproj file</span></span>

<span data-ttu-id="cfc4e-112">請開啟專案的 .csproj 檔案，並新增下列項目：</span><span class="sxs-lookup"><span data-stu-id="cfc4e-112">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="cfc4e-113">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>。</span><span class="sxs-lookup"><span data-stu-id="cfc4e-113">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfc4e-114">範例</span><span class="sxs-lookup"><span data-stu-id="cfc4e-114">Example</span></span>  
 <span data-ttu-id="cfc4e-115">針對 Unsafe 模式編譯 `in.cs`：</span><span class="sxs-lookup"><span data-stu-id="cfc4e-115">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="cfc4e-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="cfc4e-116">See Also</span></span>  
 [<span data-ttu-id="cfc4e-117">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="cfc4e-117">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="cfc4e-118">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="cfc4e-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
