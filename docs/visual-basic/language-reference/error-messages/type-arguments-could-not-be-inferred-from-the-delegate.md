---
title: 無法從委派推斷型別引數
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: f29e92c8245e33c0418d9a387070b03f645c331e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362744"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>無法從委派推斷型別引數
指派陳述式使用 `AddressOf` 將泛型程序的位址指派給委派，但未將任何類型引數提供給泛型程序。  
  
 通常，當您叫用泛型類型時，會針對泛型類型所定義的每個類型參數提供類型引數。 如果您未提供任何類型引數，編譯器會嘗試推斷要傳遞給類型參數的類型。 如果內容未提供足夠的資訊讓編譯器推斷類型，則會產生錯誤。  
  
 **錯誤識別碼：** BC36564  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 在 `AddressOf` 運算式中指定泛型程序的類型引數。  
  
## <a name="see-also"></a>另請參閱

- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [AddressOf 運算子](../operators/addressof-operator.md)
- [Generic Procedures in Visual Basic](../../programming-guide/language-features/data-types/generic-procedures.md)
- [Type List](../statements/type-list.md)
- [擴充方法](../../programming-guide/language-features/procedures/extension-methods.md)
