---
title: "-checked (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /checked
dev_langs:
- CSharp
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: bb28bf28c3d8a426322e1c1795941de7e9aa4bf6
ms.openlocfilehash: 985f150e17aef197f41b4c333758ab653d87d60a
ms.contentlocale: zh-tw
ms.lasthandoff: 05/31/2017

---
# <a name="checked-c-compiler-options"></a><span data-ttu-id="d1eda-102">/checked (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="d1eda-102">/checked (C# Compiler Options)</span></span>
<span data-ttu-id="d1eda-103">**/checked** 選項會指定產生超出該資料型別範圍之值且不在 [checked](../../../csharp/language-reference/keywords/checked.md) 或 [unchecked](../../../csharp/language-reference/keywords/unchecked.md) 關鍵字範圍內的整數算術陳述式是否導致執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d1eda-103">The **/checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../../../csharp/language-reference/keywords/checked.md) or [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1eda-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1eda-104">Syntax</span></span>  
  
```console  
/checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="d1eda-105">備註</span><span class="sxs-lookup"><span data-stu-id="d1eda-105">Remarks</span></span>  
 <span data-ttu-id="d1eda-106">在 `checked` 或 `unchecked` 關鍵字範圍內的整數算術陳述式不一定會有 **/checked** 選項的效果。</span><span class="sxs-lookup"><span data-stu-id="d1eda-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **/checked** option.</span></span>  
  
 <span data-ttu-id="d1eda-107">如果不在 `checked` 或 `unchecked` 關鍵字範圍內的整數算術陳述式產生超出該資料型別範圍的值，並在編譯時使用 **/checked+** (**/checked**)，則陳述式會在執行階段導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d1eda-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **/checked+** (**/checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="d1eda-108">如果在編譯時使用 **/checked-**，則該陳述式不會在執行階段導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d1eda-108">If **/checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="d1eda-109">這個選項的預設值是 **/checked-**。</span><span class="sxs-lookup"><span data-stu-id="d1eda-109">The default value for this option is **/checked-**.</span></span> <span data-ttu-id="d1eda-110">使用 **/checked-** 的其中一個案例是建置大型應用程式。</span><span class="sxs-lookup"><span data-stu-id="d1eda-110">One scenario for using **/checked-** is in building large applications.</span></span> <span data-ttu-id="d1eda-111">自動化工具有時是用來建置這類應用程式，而且這類工具可能會將 **/checked** 自動設為 +。</span><span class="sxs-lookup"><span data-stu-id="d1eda-111">Sometimes automated tools are used to build such applications, and such a tool might automatically set **/checked** to +.</span></span> <span data-ttu-id="d1eda-112">您可以指定 **/checked-** 來覆寫工具的全域預設值。</span><span class="sxs-lookup"><span data-stu-id="d1eda-112">You can override the tool's global default by specifying **/checked-**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d1eda-113">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="d1eda-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="d1eda-114">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="d1eda-114">Open the project's **Properties** page.</span></span> <span data-ttu-id="d1eda-115">如需詳細資訊，請參閱[專案設計工具、建置頁 (C#)](https://docs.microsoft.com/visualstudio/ide/reference/build-page-project-designer-csharp)。</span><span class="sxs-lookup"><span data-stu-id="d1eda-115">For more information, see [Build Page, Project Designer (C#)](https://docs.microsoft.com/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="d1eda-116">按一下 [建置] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="d1eda-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="d1eda-117">按一下 [ **進階** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d1eda-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="d1eda-118">修改 [檢查算術溢位/反向溢位] 屬性。</span><span class="sxs-lookup"><span data-stu-id="d1eda-118">Modify the **Check for arithmetic overflow/underflow** property.</span></span>  
  
 <span data-ttu-id="d1eda-119">若要以程式設計方式存取這個編譯器選項，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>。</span><span class="sxs-lookup"><span data-stu-id="d1eda-119">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1eda-120">範例</span><span class="sxs-lookup"><span data-stu-id="d1eda-120">Example</span></span>  
 <span data-ttu-id="d1eda-121">下列命令會編譯 `t2.cs`。</span><span class="sxs-lookup"><span data-stu-id="d1eda-121">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="d1eda-122">在命令中使用 `/checked` 會指定檔案中不在 `checked` 或 `unchecked` 關鍵字範圍內且產生超出該資料型別範圍之值的任何整數算術陳述式，都會在執行階段導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d1eda-122">The use of `/checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs /checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1eda-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1eda-123">See Also</span></span>  
 <span data-ttu-id="d1eda-124">[C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="d1eda-124">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
<span data-ttu-id="d1eda-125"> [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span><span class="sxs-lookup"><span data-stu-id="d1eda-125"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span></span>  
<span data-ttu-id="d1eda-126"> [專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)</span><span class="sxs-lookup"><span data-stu-id="d1eda-126"> [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)</span></span>
