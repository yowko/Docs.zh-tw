---
title: "'<elementname>' 已經過時 (Visual Basic 警告)"
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: d7d3d86f89ef3b76e958707dd0be2dce8a3e9bf2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64659809"
---
# <a name="elementname-is-obsolete-visual-basic-warning"></a><span data-ttu-id="1a650-102">'\<項目名稱 >' 已經過時 （Visual Basic 警告）</span><span class="sxs-lookup"><span data-stu-id="1a650-102">'\<elementname>' is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="1a650-103">陳述式嘗試存取已使用 <xref:System.ObsoleteAttribute> 屬性和指示詞標記以視為警告的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="1a650-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="1a650-104">您可以將任何程式設計項目標記為不再使用，方法是對其套用 <xref:System.ObsoleteAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="1a650-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="1a650-105">如果您這麼做，則可以將屬性 (attribute) 的 <xref:System.ObsoleteAttribute.IsError%2A> 屬性 (property) 設定為 `True` 或 `False`。</span><span class="sxs-lookup"><span data-stu-id="1a650-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="1a650-106">如果您將它設定為 `True`，則編譯器會將使用這個項目的嘗試視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="1a650-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="1a650-107">如果您將它設定為 `False`，或讓它預設為 `False`，則在嘗試使用該項目時，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="1a650-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="1a650-108">根據預設，這個訊息是一個警告，因為 <xref:System.ObsoleteAttribute.IsError%2A> 的 <xref:System.ObsoleteAttribute> 屬性是 `False`。</span><span class="sxs-lookup"><span data-stu-id="1a650-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="1a650-109">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="1a650-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="1a650-110">**錯誤 ID:** BC40008</span><span class="sxs-lookup"><span data-stu-id="1a650-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1a650-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1a650-111">To correct this error</span></span>  
  
- <span data-ttu-id="1a650-112">確定原始程式碼參考正確拼寫項目名稱。</span><span class="sxs-lookup"><span data-stu-id="1a650-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a650-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a650-113">See also</span></span>

- [<span data-ttu-id="1a650-114">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="1a650-114">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
