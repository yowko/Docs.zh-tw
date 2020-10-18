---
title: 基底類別 '<baseclassname>' 已實作 '<interfacename>.<membername>'。 假設要重新實作 <type>
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 8137f6b1712b6a0752a991f5a3d598b5f958252c
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162813"
---
# <a name="bc42015-interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a>BC42015： ' \<interfacename> . \<membername> ' 已經由基類 ' ' 實作為 \<baseclassname> 。 假設要重新實作 \<type>

衍生類別中的屬性、程式或事件使用 `Implements` 子句來指定已在基類中執行的介面成員。

 衍生類別可以重新實作透過其基底類別所實作的介面成員。 這與覆寫基底類別實作不同。 如需詳細資訊，請參閱 [Implements](../statements/implements-clause.md)。

 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。

 **錯誤識別碼：** BC42015

## <a name="to-correct-this-error"></a>更正這個錯誤

- 如果您要重新實作介面成員，則不需要採取任何動作。 除非您使用 `MyBase` 關鍵字來存取基類執行，否則衍生類別中的程式碼會存取根據成員。

- 如果您不要重新實作介面成員，請從屬性、程序或事件宣告中移除 `Implements` 子句。

## <a name="see-also"></a>另請參閱

- [介面](../../programming-guide/language-features/interfaces/index.md)
