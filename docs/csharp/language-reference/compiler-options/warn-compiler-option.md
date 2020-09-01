---
description: -warn (C# 編譯器選項)
title: -warn (C# 編譯器選項)
ms.date: 07/20/2015
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
ms.custom: updateeachrelease
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: 55e80d0bd05e2119154210503bb277d743050e18
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139069"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="b7eaf-103">-warn (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="b7eaf-103">-warn (C# Compiler Options)</span></span>
<span data-ttu-id="b7eaf-104">**-warn** 選項指定要針對編譯器顯示的警告層級。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-104">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7eaf-105">語法</span><span class="sxs-lookup"><span data-stu-id="b7eaf-105">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="b7eaf-106">引數</span><span class="sxs-lookup"><span data-stu-id="b7eaf-106">Arguments</span></span>  
 `option`  
 <span data-ttu-id="b7eaf-107">您想要針對編譯顯示的警告層級：較低的數字只會顯示高嚴重性警告；較高的數字則顯示更多的警告。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-107">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="b7eaf-108">此值必須為零或正整數：</span><span class="sxs-lookup"><span data-stu-id="b7eaf-108">The value must be zero or a positive integer:</span></span>

|<span data-ttu-id="b7eaf-109">警告層級</span><span class="sxs-lookup"><span data-stu-id="b7eaf-109">Warning level</span></span>|<span data-ttu-id="b7eaf-110">意義</span><span class="sxs-lookup"><span data-stu-id="b7eaf-110">Meaning</span></span>|
|-------------------|-------------|
|<span data-ttu-id="b7eaf-111">0</span><span class="sxs-lookup"><span data-stu-id="b7eaf-111">0</span></span>|<span data-ttu-id="b7eaf-112">關閉發出所有警告訊息。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-112">Turns off emission of all warning messages.</span></span>|
|<span data-ttu-id="b7eaf-113">1</span><span class="sxs-lookup"><span data-stu-id="b7eaf-113">1</span></span>|<span data-ttu-id="b7eaf-114">顯示嚴重警告訊息。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-114">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="b7eaf-115">2</span><span class="sxs-lookup"><span data-stu-id="b7eaf-115">2</span></span>|<span data-ttu-id="b7eaf-116">顯示層級 1 警告，以及特定較不嚴重的警告，例如隱藏類別成員的警告。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-116">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="b7eaf-117">3</span><span class="sxs-lookup"><span data-stu-id="b7eaf-117">3</span></span>|<span data-ttu-id="b7eaf-118">顯示層級 2 警告，以及特定較不嚴重的警告，例如一律評估為 `true` 或 `false` 之運算式的警告。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-118">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="b7eaf-119">4 (預設值)</span><span class="sxs-lookup"><span data-stu-id="b7eaf-119">4 (the default)</span></span>|<span data-ttu-id="b7eaf-120">顯示所有層級 3 警告以及告知性警告。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-120">Displays all level 3 warnings plus informational warnings.</span></span>|
|<span data-ttu-id="b7eaf-121">5</span><span class="sxs-lookup"><span data-stu-id="b7eaf-121">5</span></span>|<span data-ttu-id="b7eaf-122">顯示層級4警告以及編譯器隨附的 [其他警告](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) （c # 9.0）。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-122">Displays level 4 warnings plus [additional warnings](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) from the compiler shipped with C# 9.0.</span></span>|
|<span data-ttu-id="b7eaf-123">大於5</span><span class="sxs-lookup"><span data-stu-id="b7eaf-123">Greater than 5</span></span>|<span data-ttu-id="b7eaf-124">任何大於5的值都會被視為5。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-124">Any value greater than 5 will be treated as 5.</span></span> <span data-ttu-id="b7eaf-125">您通常會將任意大數值 (例如， `9999`) ，以確保當編譯器以新的警告層級更新時，一律會出現所有警告。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-125">You generally put arbitrary large value (for example, `9999`) to make sure you always have all warnings if the compiler is updated with new warning levels.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="b7eaf-126">備註</span><span class="sxs-lookup"><span data-stu-id="b7eaf-126">Remarks</span></span>  
 <span data-ttu-id="b7eaf-127">若要取得錯誤或警告資訊，您可以查閱 [說明索引] 中的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-127">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="b7eaf-128">如需取得錯誤或警告資訊的其他方式，請參閱 [C# 編譯器錯誤](../compiler-messages/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-128">For other ways to get information about an error or warning, see [C# Compiler Errors](../compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="b7eaf-129">使用 [-warnaserror](./warnaserror-compiler-option.md) 將所有警告都視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-129">Use [-warnaserror](./warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="b7eaf-130">使用 [-nowarn](./nowarn-compiler-option.md) 停用特定警告。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-130">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="b7eaf-131">**-w** 是 **-warn** 的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-131">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="b7eaf-132">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="b7eaf-132">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="b7eaf-133">開啟專案的 [屬性]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-133">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="b7eaf-134">按一下 [建置]\*\*\*\* 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-134">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="b7eaf-135">修改 [警告層級]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-135">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="b7eaf-136">如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>。</span><span class="sxs-lookup"><span data-stu-id="b7eaf-136">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7eaf-137">範例</span><span class="sxs-lookup"><span data-stu-id="b7eaf-137">Example</span></span>  
 <span data-ttu-id="b7eaf-138">編譯 `in.cs`，並讓編譯器只顯示層級 1 警告：</span><span class="sxs-lookup"><span data-stu-id="b7eaf-138">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7eaf-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7eaf-139">See also</span></span>

- [<span data-ttu-id="b7eaf-140">C # 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="b7eaf-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b7eaf-141">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="b7eaf-141">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
