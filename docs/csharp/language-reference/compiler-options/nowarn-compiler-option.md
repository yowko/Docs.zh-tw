---
title: -nowarn (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: b455a2f719e7350c51cf4a1f095d4669529d0e5e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592803"
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="d225c-102">-nowarn (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="d225c-102">-nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="d225c-103">**-nowarn** 選項可讓您隱藏編譯器不顯示一或多個警告。</span><span class="sxs-lookup"><span data-stu-id="d225c-103">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="d225c-104">請以逗點分隔多個警告編號。</span><span class="sxs-lookup"><span data-stu-id="d225c-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d225c-105">語法</span><span class="sxs-lookup"><span data-stu-id="d225c-105">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d225c-106">引數</span><span class="sxs-lookup"><span data-stu-id="d225c-106">Arguments</span></span>  
 <span data-ttu-id="d225c-107">`number1`、 `number2`</span><span class="sxs-lookup"><span data-stu-id="d225c-107">`number1`, `number2`</span></span>  
 <span data-ttu-id="d225c-108">您想要編譯器隱藏的警告編號。</span><span class="sxs-lookup"><span data-stu-id="d225c-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d225c-109">備註</span><span class="sxs-lookup"><span data-stu-id="d225c-109">Remarks</span></span>  
 <span data-ttu-id="d225c-110">您應該只要指定警告識別項的數值部分。</span><span class="sxs-lookup"><span data-stu-id="d225c-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="d225c-111">例如，如果您想要隱藏 CS0028，您可以指定 `-nowarn:28`。</span><span class="sxs-lookup"><span data-stu-id="d225c-111">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="d225c-112">編譯器會以無訊息方式略過傳遞給 `-nowarn` 的警告編號，它在舊版中有效但已自編譯器移除。</span><span class="sxs-lookup"><span data-stu-id="d225c-112">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="d225c-113">例如，CS0679 在 Visual Studio .NET 2002 的編譯器中有效，但後來已移除。</span><span class="sxs-lookup"><span data-stu-id="d225c-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="d225c-114">`-nowarn` 選項無法隱藏下列警告︰</span><span class="sxs-lookup"><span data-stu-id="d225c-114">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
- <span data-ttu-id="d225c-115">編譯器警告 (層級 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="d225c-115">Compiler Warning (level 1) CS2002</span></span>  
  
- <span data-ttu-id="d225c-116">編譯器警告 (層級 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="d225c-116">Compiler Warning (level 1) CS2023</span></span>  
  
- <span data-ttu-id="d225c-117">編譯器警告 (層級 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="d225c-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d225c-118">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="d225c-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="d225c-119">開啟專案的 [屬性]  頁面。</span><span class="sxs-lookup"><span data-stu-id="d225c-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="d225c-120">如需詳細資料，請參閱[專案設計工具、建置頁 (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)。</span><span class="sxs-lookup"><span data-stu-id="d225c-120">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="d225c-121">按一下 [建置] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="d225c-121">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="d225c-122">修改**隱藏警告**屬性。</span><span class="sxs-lookup"><span data-stu-id="d225c-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="d225c-123">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>。</span><span class="sxs-lookup"><span data-stu-id="d225c-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d225c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d225c-124">See also</span></span>

- [<span data-ttu-id="d225c-125">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="d225c-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="d225c-126">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="d225c-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="d225c-127">C# 編譯器錯誤</span><span class="sxs-lookup"><span data-stu-id="d225c-127">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
