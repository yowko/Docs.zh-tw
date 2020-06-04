---
title: 基底類別 '<baseclassname>' 已實作 '<interfacename>.<membername>'。 假設要重新實作 <type>
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 6525ae08b90cc530a8f6a469d35d9ab8c27fb5e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402820"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a>基底類別 '\<baseclassname>' 已實作 '\<interfacename>.\<membername>'。 假設要重新實作 \<type>
衍生類別中的屬性、程式或事件 `Implements` 會使用子句來指定已在基類中實作為介面成員。  
  
 衍生類別可以重新實作透過其基底類別所實作的介面成員。 這與覆寫基底類別實作不同。 如需詳細資訊，請參閱 [Implements](../statements/implements-clause.md)。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼：** BC42015  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 如果您要重新實作介面成員，則不需要採取任何動作。 除非您使用 `MyBase` 關鍵字來存取基類執行，否則衍生類別中的程式碼會存取根據重新實作成員。  
  
- 如果您不要重新實作介面成員，請從屬性、程序或事件宣告中移除 `Implements` 子句。  
  
## <a name="see-also"></a>另請參閱

- [介面](../../programming-guide/language-features/interfaces/index.md)
