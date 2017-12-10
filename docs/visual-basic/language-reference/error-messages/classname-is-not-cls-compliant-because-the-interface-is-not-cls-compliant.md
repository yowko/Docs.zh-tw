---
title: "&#39;&lt;classname&gt;&#39; 不符合 CLS 標準，因為介面 &#39;&lt;介面名稱&gt;&#39; 該方法實作不符合 CLS 標準"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords: BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 60c41332d3a5d93b05df906eefdeeb0d1b67e638
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2017
---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a><span data-ttu-id="b9291-102">&#39;&lt;classname&gt;&#39; 不符合 CLS 標準，因為介面 &#39;&lt;介面名稱&gt;&#39; 該方法實作不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="b9291-102">&#39;&lt;classname&gt;&#39; is not CLS-compliant because the interface &#39;&lt;interfacename&gt;&#39; it implements is not CLS-compliant</span></span>
<span data-ttu-id="b9291-103">當類別或介面衍生自或實作標記為 `<CLSCompliant(True)>` 或未標記的類型時，則標記為 `<CLSCompliant(False)>` 。</span><span class="sxs-lookup"><span data-stu-id="b9291-103">A class or interface is marked as `<CLSCompliant(True)>` when it derives from or implements a type that is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="b9291-104">類別或介面若要符合[語言獨立性以及與語言無關的元件](../../../../docs/standard/language-independence-and-language-independent-components.md)（cls） 標準，其整個繼承階層架構必須相容。</span><span class="sxs-lookup"><span data-stu-id="b9291-104">For a class or interface to be compliant with the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), its entire inheritance hierarchy must be compliant.</span></span> <span data-ttu-id="b9291-105">這表示它直接或間接繼承的每個類型都必須符合標準。</span><span class="sxs-lookup"><span data-stu-id="b9291-105">That means every type from which it inherits, directly or indirectly, must be compliant.</span></span> <span data-ttu-id="b9291-106">同樣地，如果類別實作一或多個介面，則它們在整個繼承階層都必須符合標準。</span><span class="sxs-lookup"><span data-stu-id="b9291-106">Similarly, if a class implements one or more interfaces, they must all be compliant throughout their inheritance hierarchies.</span></span>  
  
 <span data-ttu-id="b9291-107">將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False` ，表示符合標準或不符合標準。</span><span class="sxs-lookup"><span data-stu-id="b9291-107">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="b9291-108">這個參數沒有預設值，您必須提供值。</span><span class="sxs-lookup"><span data-stu-id="b9291-108">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="b9291-109">如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。</span><span class="sxs-lookup"><span data-stu-id="b9291-109">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="b9291-110">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="b9291-110">By default, this message is a warning.</span></span> <span data-ttu-id="b9291-111">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="b9291-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b9291-112">**錯誤 ID:** BC40029</span><span class="sxs-lookup"><span data-stu-id="b9291-112">**Error ID:** BC40029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b9291-113">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b9291-113">To correct this error</span></span>  
  
-   <span data-ttu-id="b9291-114">如果您必須符合 CLS 標準，請在不同的繼承階層或實作配置內定義這個類型。</span><span class="sxs-lookup"><span data-stu-id="b9291-114">If you require CLS compliance, define this type within a different inheritance hierarchy or implementation scheme.</span></span>  
  
-   <span data-ttu-id="b9291-115">如果您想要將這個類型保留在其目前繼承階層或實作配置內，請從其定義移除 <xref:System.CLSCompliantAttribute> 或將其標記為 `<CLSCompliant(False)>`。</span><span class="sxs-lookup"><span data-stu-id="b9291-115">If you require that this type remain within its current inheritance hierarchy or implementation scheme, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9291-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9291-116">See Also</span></span>  
 [<span data-ttu-id="b9291-117">\<PAVE OVER > 撰寫符合 CLS 標準的程式碼</span><span class="sxs-lookup"><span data-stu-id="b9291-117">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
