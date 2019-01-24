---
title: '&#39;&lt;interfacename&gt;。&lt;membername&gt; &#39;的基底類別已實作&#39;&lt;基&gt;&#39;。 重新實作&lt;型別&gt;假設'
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 22a3bd4e8c09c0d070e7fa5e75571a7215c3a274
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507196"
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a>&#39;&lt;interfacename&gt;。&lt;membername&gt; &#39;的基底類別已實作&#39;&lt;基&gt;&#39;。 重新實作&lt;型別&gt;假設
屬性、 程序或在衍生類別中的事件使用`Implements`子句指定的基底類別中已實作介面成員。  
  
 衍生類別可以重新實作透過其基底類別所實作的介面成員。 這與覆寫基底類別實作不同。 如需詳細資訊，請參閱 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC42015  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果您要重新實作介面成員，則不需要採取任何動作。 在衍生類別中的程式碼會存取重新實作的成員，除非您使用`MyBase`關鍵字存取基底類別實作。  
  
-   如果您不要重新實作介面成員，請從屬性、程序或事件宣告中移除 `Implements` 子句。  
  
## <a name="see-also"></a>另請參閱
- [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
