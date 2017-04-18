---
title: "&quot;&lt;classname&gt;&quot; 不符合 CLS 標準，因為介面 &quot;&lt;interfacename&gt;&quot; 它會實作不符合 CLS 標準 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40029
- vbc40029
dev_langs:
- VB
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1e5c948ed5ddeaa2f8a8efd4aa83a2539cc862f3
ms.lasthandoff: 03/13/2017

---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a>'&lt;classname&gt;' 不符合 CLS 標準，因為介面 '&lt;interfacename&gt;' 它會實作不符合 CLS 標準
當類別或介面衍生自或實作標記為 `<CLSCompliant(True)>` 或未標記的類型時，則標記為 `<CLSCompliant(False)>` 。  
  
 類別或介面，以符合[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3)(CLS)，其整個繼承階層架構必須相容。 這表示它直接或間接繼承的每個類型都必須符合規範。 同樣地，如果類別實作一或多個介面，則它們在整個繼承階層都必須符合規範。  
  
 當您將套用<xref:System.CLSCompliantAttribute>程式設計項目，您可以設定屬性的`isCompliant`參數為`True`或`False`表示相容或不相容。</xref:System.CLSCompliantAttribute> 這個參數沒有預設值，您必須提供值。  
  
 如果您不會套用<xref:System.CLSCompliantAttribute>的項目，它會被視為不相容。</xref:System.CLSCompliantAttribute>  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼︰** BC40029  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果您必須符合 CLS 規範，請在不同的繼承階層或實作配置內定義這個類型。  
  
-   如果您需要此類型會保留其目前的繼承階層架構或實作配置中，移除<xref:System.CLSCompliantAttribute>從其定義或標示為`<CLSCompliant(False)>`。</xref:System.CLSCompliantAttribute>  
  
## <a name="see-also"></a>另請參閱  
 [\<PAVE OVER > 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
