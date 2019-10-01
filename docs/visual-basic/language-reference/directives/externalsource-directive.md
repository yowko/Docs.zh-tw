---
title: '#ExternalSource 指示詞（Visual Basic）'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: ac7096e998dd8d2a416dc739e1d7625e1abff7a6
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696830"
---
# <a name="externalsource-directive"></a><span data-ttu-id="a6dd6-102">#ExternalSource 指示詞</span><span class="sxs-lookup"><span data-stu-id="a6dd6-102">#ExternalSource Directive</span></span>
<span data-ttu-id="a6dd6-103">表示原始程式程式碼與來源外部文字之間的對應。</span><span class="sxs-lookup"><span data-stu-id="a6dd6-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6dd6-104">語法</span><span class="sxs-lookup"><span data-stu-id="a6dd6-104">Syntax</span></span>  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="a6dd6-105">組件</span><span class="sxs-lookup"><span data-stu-id="a6dd6-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="a6dd6-106">外部來源的路徑。</span><span class="sxs-lookup"><span data-stu-id="a6dd6-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="a6dd6-107">外部來源第一行的行號。</span><span class="sxs-lookup"><span data-stu-id="a6dd6-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="a6dd6-108">外部來源中發生錯誤的行。</span><span class="sxs-lookup"><span data-stu-id="a6dd6-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="a6dd6-109">終止 `#ExternalSource` 區塊。</span><span class="sxs-lookup"><span data-stu-id="a6dd6-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6dd6-110">備註</span><span class="sxs-lookup"><span data-stu-id="a6dd6-110">Remarks</span></span>  
 <span data-ttu-id="a6dd6-111">這個指示詞僅供編譯器和偵錯工具使用。</span><span class="sxs-lookup"><span data-stu-id="a6dd6-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="a6dd6-112">原始程式檔可能包含外部來源指示詞，這表示原始程式檔中的特定程式程式碼與來源外部的文字之間的對應，例如 .aspx 檔案。</span><span class="sxs-lookup"><span data-stu-id="a6dd6-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="a6dd6-113">如果在編譯期間于指定的原始程式碼中遇到錯誤，則會將它們識別為來自外部來源。</span><span class="sxs-lookup"><span data-stu-id="a6dd6-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="a6dd6-114">外部來源指示詞不會影響編譯，而且無法加以嵌套。</span><span class="sxs-lookup"><span data-stu-id="a6dd6-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="a6dd6-115">它們僅供應用程式內部使用。</span><span class="sxs-lookup"><span data-stu-id="a6dd6-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6dd6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6dd6-116">See also</span></span>

- [<span data-ttu-id="a6dd6-117">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="a6dd6-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
