---
title: "-warn (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6a1f2c55aa078adb213a93dc5aff7ced40793bfa
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="d76e7-102">-warn (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="d76e7-102">-warn (C# Compiler Options)</span></span>
<span data-ttu-id="d76e7-103">**-warn** 選項指定要針對編譯器顯示的警告層級。</span><span class="sxs-lookup"><span data-stu-id="d76e7-103">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d76e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="d76e7-104">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="d76e7-105">引數</span><span class="sxs-lookup"><span data-stu-id="d76e7-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="d76e7-106">您想要針對編譯顯示的警告層級：較低的數字只會顯示高嚴重性警告；較高的數字則顯示更多的警告。</span><span class="sxs-lookup"><span data-stu-id="d76e7-106">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="d76e7-107">有效值為 0-4：</span><span class="sxs-lookup"><span data-stu-id="d76e7-107">Valid values are 0-4:</span></span>  
  
|<span data-ttu-id="d76e7-108">警告層級</span><span class="sxs-lookup"><span data-stu-id="d76e7-108">Warning level</span></span>|<span data-ttu-id="d76e7-109">意義</span><span class="sxs-lookup"><span data-stu-id="d76e7-109">Meaning</span></span>|  
|-------------------|-------------|  
|<span data-ttu-id="d76e7-110">0</span><span class="sxs-lookup"><span data-stu-id="d76e7-110">0</span></span>|<span data-ttu-id="d76e7-111">關閉發出所有警告訊息。</span><span class="sxs-lookup"><span data-stu-id="d76e7-111">Turns off emission of all warning messages.</span></span>|  
|<span data-ttu-id="d76e7-112">1</span><span class="sxs-lookup"><span data-stu-id="d76e7-112">1</span></span>|<span data-ttu-id="d76e7-113">顯示嚴重警告訊息。</span><span class="sxs-lookup"><span data-stu-id="d76e7-113">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="d76e7-114">2</span><span class="sxs-lookup"><span data-stu-id="d76e7-114">2</span></span>|<span data-ttu-id="d76e7-115">顯示層級 1 警告，以及特定較不嚴重的警告，例如隱藏類別成員的警告。</span><span class="sxs-lookup"><span data-stu-id="d76e7-115">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="d76e7-116">3</span><span class="sxs-lookup"><span data-stu-id="d76e7-116">3</span></span>|<span data-ttu-id="d76e7-117">顯示層級 2 警告，以及特定較不嚴重的警告，例如一律評估為 `true` 或 `false` 之運算式的警告。</span><span class="sxs-lookup"><span data-stu-id="d76e7-117">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="d76e7-118">4 (預設值)</span><span class="sxs-lookup"><span data-stu-id="d76e7-118">4 (the default)</span></span>|<span data-ttu-id="d76e7-119">顯示所有層級 3 警告以及告知性警告。</span><span class="sxs-lookup"><span data-stu-id="d76e7-119">Displays all level 3 warnings plus informational warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d76e7-120">備註</span><span class="sxs-lookup"><span data-stu-id="d76e7-120">Remarks</span></span>  
 <span data-ttu-id="d76e7-121">若要取得錯誤或警告資訊，您可以查閱 [說明索引] 中的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d76e7-121">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="d76e7-122">如需取得錯誤或警告資訊的其他方式，請參閱 [C# 編譯器錯誤](../../../csharp/language-reference/compiler-messages/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d76e7-122">For other ways to get information about an error or warning, see [C# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="d76e7-123">使用 [-warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) 將所有警告都視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="d76e7-123">Use [-warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="d76e7-124">使用 [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) 停用特定警告。</span><span class="sxs-lookup"><span data-stu-id="d76e7-124">Use [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="d76e7-125">**-w** 是 **-warn** 的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="d76e7-125">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d76e7-126">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="d76e7-126">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="d76e7-127">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="d76e7-127">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="d76e7-128">按一下 [建置] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="d76e7-128">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="d76e7-129">修改 [警告層級] 屬性。</span><span class="sxs-lookup"><span data-stu-id="d76e7-129">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="d76e7-130">如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>。</span><span class="sxs-lookup"><span data-stu-id="d76e7-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d76e7-131">範例</span><span class="sxs-lookup"><span data-stu-id="d76e7-131">Example</span></span>  
 <span data-ttu-id="d76e7-132">編譯 `in.cs`，並讓編譯器只顯示層級 1 警告：</span><span class="sxs-lookup"><span data-stu-id="d76e7-132">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d76e7-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="d76e7-133">See Also</span></span>  
 [<span data-ttu-id="d76e7-134">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="d76e7-134">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="d76e7-135">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="d76e7-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
