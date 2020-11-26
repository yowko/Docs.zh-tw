---
description: -unsafe (C# 編譯器選項)
title: -unsafe (C# 編譯器選項)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 0f6d94dd25a020d96430746c4b5e7aefd0f679da
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "89140837"
---
# <a name="-unsafe-c-compiler-options"></a><span data-ttu-id="6c4a9-103">-unsafe (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="6c4a9-103">-unsafe (C# Compiler Options)</span></span>

<span data-ttu-id="6c4a9-104">**-unsafe** 編譯器選項允許程式碼使用 [unsafe](../keywords/unsafe.md) 關鍵字來進行編譯。</span><span class="sxs-lookup"><span data-stu-id="6c4a9-104">The **-unsafe** compiler option allows code that uses the [unsafe](../keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c4a9-105">語法</span><span class="sxs-lookup"><span data-stu-id="6c4a9-105">Syntax</span></span>  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="6c4a9-106">備註</span><span class="sxs-lookup"><span data-stu-id="6c4a9-106">Remarks</span></span>

<span data-ttu-id="6c4a9-107">如需 Unsafe 程式碼的詳細資訊，請參閱 [Unsafe 程式碼和指標](../../programming-guide/unsafe-code-pointers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="6c4a9-107">For more information about unsafe code, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6c4a9-108">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="6c4a9-108">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="6c4a9-109">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="6c4a9-109">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="6c4a9-110">按一下 [建置] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="6c4a9-110">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="6c4a9-111">選取 [容許 Unsafe 程式碼] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6c4a9-111">Select the **Allow Unsafe Code** check box.</span></span>  
  
### <a name="to-add-this-option-in-a-csproj-file"></a><span data-ttu-id="6c4a9-112">在 csproj 檔案中新增此選項</span><span class="sxs-lookup"><span data-stu-id="6c4a9-112">To add this option in a csproj file</span></span>

<span data-ttu-id="6c4a9-113">請開啟專案的 .csproj 檔案，並新增下列項目：</span><span class="sxs-lookup"><span data-stu-id="6c4a9-113">Open the .csproj file for a project, and add the following elements:</span></span>

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 <span data-ttu-id="6c4a9-114">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>。</span><span class="sxs-lookup"><span data-stu-id="6c4a9-114">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c4a9-115">範例</span><span class="sxs-lookup"><span data-stu-id="6c4a9-115">Example</span></span>

<span data-ttu-id="6c4a9-116">針對 Unsafe 模式編譯 `in.cs`：</span><span class="sxs-lookup"><span data-stu-id="6c4a9-116">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c4a9-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c4a9-117">See also</span></span>

- [<span data-ttu-id="6c4a9-118">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="6c4a9-118">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="6c4a9-119">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="6c4a9-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
