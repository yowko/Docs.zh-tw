---
title: 必須是 'Optional'
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 9c717cef2052722563e04595ef7a808ea103a75d
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159816"
---
# <a name="bc30202-optional-expected"></a>BC30202：必須為 ' Optional '

程式聲明中的選擇性引數後面接著必要的引數。 選擇性引數後面的每個引數也必須是選擇性的。

 **錯誤識別碼：** BC30202

## <a name="to-correct-this-error"></a>更正這個錯誤

- 如果需要引數，請將其移至引數清單中的第一個選擇性引數前面。

- 如果引數是選擇性的，請使用 `Optional` 關鍵字。

## <a name="see-also"></a>另請參閱

- [選擇性參數](../../programming-guide/language-features/procedures/optional-parameters.md)
