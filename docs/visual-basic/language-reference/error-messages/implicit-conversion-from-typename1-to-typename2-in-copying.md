---
title: 在將 'ByRef' 參數 '<typename1>' 的值複製回相對應的引數時，將 '<typename2>' 隱含轉換至 '<parametername>'
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: a95a4b792742efcc165f7c7a9592582d34618f11
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162800"
---
# <a name="bc41999-implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a>BC41999： \<typename1> 將 \<typename2> ' ByRef ' 參數 ' ' 的值複製 \<parametername> 回相符的引數時，從 ' ' 隱含轉換成 ' '。

使用與其對應參數不同類型的 [ByRef](../modifiers/byref.md) 引數來呼叫程式。

 如果您傳遞引數 `ByRef` ，Visual Basic 有時會將引數值複製至程式中的區域變數，而不是傳遞參考。 在這種情況下，當程式傳回時，Visual Basic 必須接著將區域變數值複製回呼叫程式碼中的引數。

 如果將 `ByRef` 引數值複製至程序，而且引數和參數的類型相同，則不需要進行轉換。 但是，如果類型不同，Visual Basic 必須雙向轉換。 因為您無法 `CType` 在程式引數或參數上使用或其他任何轉換關鍵字，所以這類轉換一律是隱含的。

 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。

 **錯誤識別碼：** BC41999

## <a name="to-correct-this-error"></a>更正這個錯誤

- 可能的話，請使用與程式參數相同類型的呼叫引數，因此 Visual Basic 不需要進行任何轉換。

- 如果您需要呼叫引數類型與參數類型不同的程序，但不需要將值傳回給呼叫中引數，請將此參數定義為 [ByVal](../modifiers/byval.md) ，而非 `ByRef`。

## <a name="see-also"></a>另請參閱

- [程序](../../programming-guide/language-features/procedures/index.md)
- [程序參數和引數](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [以傳值和傳址方式傳遞引數](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [隱含和明確轉換](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
