---
description: -main (C# 編譯器選項)
title: -main (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 61e63de8082a335b448ffee1ae35170d3a1cf6b4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125263"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="cea79-103">-main (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="cea79-103">-main (C# Compiler Options)</span></span>

<span data-ttu-id="cea79-104">如果有多個類別包含 **Main** 方法，這個選項會指定含有程式進入點的類別。</span><span class="sxs-lookup"><span data-stu-id="cea79-104">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>

## <a name="syntax"></a><span data-ttu-id="cea79-105">語法</span><span class="sxs-lookup"><span data-stu-id="cea79-105">Syntax</span></span>

```console
-main:class
```

## <a name="arguments"></a><span data-ttu-id="cea79-106">引數</span><span class="sxs-lookup"><span data-stu-id="cea79-106">Arguments</span></span>
 `class`  
 <span data-ttu-id="cea79-107">含有 **Main** 方法的類型。</span><span class="sxs-lookup"><span data-stu-id="cea79-107">The type that contains the **Main** method.</span></span>  
 <span data-ttu-id="cea79-108">提供的類別名稱必須完整。名稱必須包括內含類別的完整命名空間，後面接著類別名稱。</span><span class="sxs-lookup"><span data-stu-id="cea79-108">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="cea79-109">例如，當 `Main` 方法位於 `MyApplication.Core` 命名空間中的 `Program` 類別時，編譯器選項必須是 `-main:MyApplication.Core.Program`。</span><span class="sxs-lookup"><span data-stu-id="cea79-109">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span>

## <a name="remarks"></a><span data-ttu-id="cea79-110">備註</span><span class="sxs-lookup"><span data-stu-id="cea79-110">Remarks</span></span>

<span data-ttu-id="cea79-111">如果編譯的 [Main](../../programming-guide/main-and-command-args/index.md) 方法中包含一個以上的型別，您可以指定哪個型別含有要作為程式進入點的 **Main** 方法。</span><span class="sxs-lookup"><span data-stu-id="cea79-111">If your compilation includes more than one type with a [Main](../../programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>

<span data-ttu-id="cea79-112">此選項適用于編譯 *.exe* 檔時。</span><span class="sxs-lookup"><span data-stu-id="cea79-112">This option is for use when compiling an *.exe* file.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="cea79-113">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="cea79-113">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="cea79-114">開啟專案的 [屬性]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="cea79-114">Open the project's **Properties** page.</span></span>

2. <span data-ttu-id="cea79-115">按一下 [應用程式]\*\*\*\* 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="cea79-115">Click the **Application** property page.</span></span>

3. <span data-ttu-id="cea79-116">修改 [啟始物件]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="cea79-116">Modify the **Startup object** property.</span></span>

    <span data-ttu-id="cea79-117">若要以程式設計方式設定這個編譯器選項，請參閱 <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>。</span><span class="sxs-lookup"><span data-stu-id="cea79-117">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>

### <a name="to-set-this-compiler-option-by-manually-editing-the-csproj-file"></a><span data-ttu-id="cea79-118">手動編輯 *.csproj* 檔案以設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="cea79-118">To set this compiler option by manually editing the *.csproj* file</span></span>

<span data-ttu-id="cea79-119">您可以藉由編輯 .csproj 檔案並在區段內加入專案來設定此選項 `StartupObject` `PropertyGroup` 。</span><span class="sxs-lookup"><span data-stu-id="cea79-119">You can set this option by editing the .csproj file and adding an element `StartupObject` inside the `PropertyGroup` section.</span></span> <span data-ttu-id="cea79-120">例如：</span><span class="sxs-lookup"><span data-stu-id="cea79-120">For example:</span></span>

```xml
  <PropertyGroup>
    ...
    <StartupObject>MyApplication.Core.Program</StartupObject>
  </PropertyGroup>
```

## <a name="example"></a><span data-ttu-id="cea79-121">範例</span><span class="sxs-lookup"><span data-stu-id="cea79-121">Example</span></span>

<span data-ttu-id="cea79-122">編譯 `t2.cs` 和 `t3.cs`，將 **Main** 方法的位置指定在 `Test2` 中：</span><span class="sxs-lookup"><span data-stu-id="cea79-122">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>

```console
csc t2.cs t3.cs -main:Test2
```

## <a name="see-also"></a><span data-ttu-id="cea79-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cea79-123">See also</span></span>

- [<span data-ttu-id="cea79-124">C # 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="cea79-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="cea79-125">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="cea79-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
