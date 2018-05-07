---
title: 不能參考&#39;&lt;名稱&gt;&#39;因為它是實值類型欄位的成員&#39;&lt;名稱&gt;&#39;類別的&#39; &lt;classname&gt; &#39;具有&#39;System.MarshalByRefObject&#39;做為基底類別
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: f44d33c9d51148e6bbcfbf5db4dbc115101df1f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a>不能參考&#39;&lt;名稱&gt;&#39;因為它是實值類型欄位的成員&#39;&lt;名稱&gt;&#39;類別的&#39; &lt;classname&gt; &#39;具有&#39;System.MarshalByRefObject&#39;做為基底類別
`System.MarshalByRefObject`類別可讓應用程式跨應用程式定義域界限支援遠端物件的存取權。 類型必須繼承自`MarshalByRejectObject`類別時跨應用程式定義域界限使用的型別。 必須不會複製物件的狀態，因為物件的成員不是他們所建立的應用程式網域外使用。  
  
 **錯誤 ID:** BC30310  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查以確定所參考的成員都是有效的參考。  
  
2.  明確限定的成員`Me`關鍵字。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.MarshalByRefObject>  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)
