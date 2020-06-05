---
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: d325d5f9fbfd132630cf280653be214a267a7a80
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400056"
---
# <a name="param-visual-basic"></a><span data-ttu-id="14f18-101">\<param> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14f18-101">\<param> (Visual Basic)</span></span>
<span data-ttu-id="14f18-102">定義參數名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="14f18-102">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14f18-103">語法</span><span class="sxs-lookup"><span data-stu-id="14f18-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="14f18-104">參數</span><span class="sxs-lookup"><span data-stu-id="14f18-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="14f18-105">方法參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="14f18-105">The name of a method parameter.</span></span> <span data-ttu-id="14f18-106">以雙引號 (" ") 將名稱括起來。</span><span class="sxs-lookup"><span data-stu-id="14f18-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="14f18-107">參數的描述。</span><span class="sxs-lookup"><span data-stu-id="14f18-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14f18-108">備註</span><span class="sxs-lookup"><span data-stu-id="14f18-108">Remarks</span></span>  
 <span data-ttu-id="14f18-109">`<param>`標記應該用於方法宣告的批註中，以描述方法的其中一個參數。</span><span class="sxs-lookup"><span data-stu-id="14f18-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="14f18-110">標記的文字 `<param>` 會出現在下列位置：</span><span class="sxs-lookup"><span data-stu-id="14f18-110">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="14f18-111">IntelliSense 的參數資訊。</span><span class="sxs-lookup"><span data-stu-id="14f18-111">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="14f18-112">如需詳細資訊，請參閱[使用 IntelliSense](/visualstudio/ide/using-intellisense)。</span><span class="sxs-lookup"><span data-stu-id="14f18-112">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="14f18-113">物件瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="14f18-113">Object Browser.</span></span> <span data-ttu-id="14f18-114">如需詳細資訊，請參閱[查看程式碼的結構](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="14f18-114">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="14f18-115">使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="14f18-115">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14f18-116">範例</span><span class="sxs-lookup"><span data-stu-id="14f18-116">Example</span></span>  
 <span data-ttu-id="14f18-117">這個範例會使用 `<param>` 標記來描述 `id` 參數。</span><span class="sxs-lookup"><span data-stu-id="14f18-117">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="14f18-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14f18-118">See also</span></span>

- [<span data-ttu-id="14f18-119">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="14f18-119">XML Comment Tags</span></span>](index.md)
