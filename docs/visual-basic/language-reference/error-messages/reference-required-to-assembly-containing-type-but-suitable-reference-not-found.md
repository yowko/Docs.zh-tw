---
title: 需要組件參考&#39; &lt;assemblyidentity&gt; &#39;包含類型&#39; &lt;typename&gt;&#39;，但是因為之間的模稜兩可而找不到適合的參考專案&#39; &lt;projectname1&gt; &#39;和&#39;&lt;專案名稱 2>&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 1a0c2a2fd235026729901153a0c0c300f914a78f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553005"
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a>需要組件參考&#39; &lt;assemblyidentity&gt; &#39;包含類型&#39; &lt;typename&gt;&#39;，但是因為之間的模稜兩可而找不到適合的參考專案&#39; &lt;projectname1&gt; &#39;和&#39;&lt;專案名稱 2>&gt;&#39;
運算式使用專案外部定義的類型 (例如類別、結構、介面、列舉或委派)。 不過，專案參考超過一個定義其類型的組件。  
  
 上述專案會產生具有相同名稱的組件。 因此，編譯器無法判斷要針對您正在存取的類型使用哪個組件。  
  
 若要存取另一個組件中定義的類型，Visual Basic 編譯器必須有該組件的參考。 這必須是單一的明確參考，不會在專案之間造成循環參考。  
  
 **錯誤 ID:** BC30969  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  決定哪些專案產生的最佳組件供專案參考。 這項決策可能會使用輕鬆存取檔案和更新頻率等準則。  
  
2.  在專案屬性中，加入包含組件之檔案的參考，而這個組件定義所使用的類型。  
  
## <a name="see-also"></a>另請參閱
- [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)
- [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
- [針對中斷參考進行疑難排解](/visualstudio/ide/troubleshooting-broken-references)
