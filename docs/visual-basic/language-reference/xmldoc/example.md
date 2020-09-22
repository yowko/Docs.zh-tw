---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 6e9f63e4d31df7790f51ae4d166b606f2c63f14b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872982"
---
# <a name="example-visual-basic"></a><span data-ttu-id="d438a-101">\<example> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d438a-101">\<example> (Visual Basic)</span></span>

<span data-ttu-id="d438a-102">指定成員的範例。</span><span class="sxs-lookup"><span data-stu-id="d438a-102">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d438a-103">語法</span><span class="sxs-lookup"><span data-stu-id="d438a-103">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d438a-104">參數</span><span class="sxs-lookup"><span data-stu-id="d438a-104">Parameters</span></span>  

 `description`  
 <span data-ttu-id="d438a-105">程式碼範例的描述。</span><span class="sxs-lookup"><span data-stu-id="d438a-105">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d438a-106">備註</span><span class="sxs-lookup"><span data-stu-id="d438a-106">Remarks</span></span>  

 <span data-ttu-id="d438a-107">`<example>`標記可讓您指定如何使用方法或其他程式庫成員的範例。</span><span class="sxs-lookup"><span data-stu-id="d438a-107">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="d438a-108">這通常牽涉到使用 [\<code>](code.md) 標記。</span><span class="sxs-lookup"><span data-stu-id="d438a-108">This commonly involves using the [\<code>](code.md) tag.</span></span>  
  
 <span data-ttu-id="d438a-109">使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。</span><span class="sxs-lookup"><span data-stu-id="d438a-109">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d438a-110">範例</span><span class="sxs-lookup"><span data-stu-id="d438a-110">Example</span></span>  

 <span data-ttu-id="d438a-111">此範例會使用 `<example>` 標記來包含使用欄位的範例 `ID` 。</span><span class="sxs-lookup"><span data-stu-id="d438a-111">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d438a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d438a-112">See also</span></span>

- [<span data-ttu-id="d438a-113">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="d438a-113">XML Comment Tags</span></span>](index.md)
