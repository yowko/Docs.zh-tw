---
title: '## ExternalSource 指示詞 (Visual Basic)'
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
ms.openlocfilehash: 39e6963c97340daab3f0ab7ad6860695f1f6c135
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747033"
---
# <a name="externalsource-directive"></a><span data-ttu-id="d84f1-102">#ExternalSource 指示詞</span><span class="sxs-lookup"><span data-stu-id="d84f1-102">#ExternalSource Directive</span></span>
<span data-ttu-id="d84f1-103">表示特定的原始程式碼行和來源外部文字之間的對應。</span><span class="sxs-lookup"><span data-stu-id="d84f1-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d84f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="d84f1-104">Syntax</span></span>  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="d84f1-105">組件</span><span class="sxs-lookup"><span data-stu-id="d84f1-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="d84f1-106">外部來源的路徑。</span><span class="sxs-lookup"><span data-stu-id="d84f1-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="d84f1-107">外部來源的第一行的行號。</span><span class="sxs-lookup"><span data-stu-id="d84f1-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="d84f1-108">外部來源中發生錯誤的行。</span><span class="sxs-lookup"><span data-stu-id="d84f1-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="d84f1-109">終止 `#ExternalSource` 區塊。</span><span class="sxs-lookup"><span data-stu-id="d84f1-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d84f1-110">備註</span><span class="sxs-lookup"><span data-stu-id="d84f1-110">Remarks</span></span>  
 <span data-ttu-id="d84f1-111">這個指示詞僅供編譯器和偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="d84f1-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="d84f1-112">原始程式檔可能包含外部來源指示詞，可指出特定程式碼中的原始程式檔行與外部來源，例如.aspx 檔案的文字之間的對應。</span><span class="sxs-lookup"><span data-stu-id="d84f1-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="d84f1-113">如果在編譯期間指定的原始程式碼中遇到錯誤，它們會識別為來自外部來源。</span><span class="sxs-lookup"><span data-stu-id="d84f1-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="d84f1-114">外部來源指示詞有對於編譯沒有作用，而且不能巢狀。</span><span class="sxs-lookup"><span data-stu-id="d84f1-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="d84f1-115">它們被供內部使用僅限應用程式。</span><span class="sxs-lookup"><span data-stu-id="d84f1-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d84f1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d84f1-116">See also</span></span>

- [<span data-ttu-id="d84f1-117">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="d84f1-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
