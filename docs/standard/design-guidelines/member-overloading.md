---
title: 成員多載
ms.date: 10/22/2008
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: 16e84f06ec388fe7e3c221f35c3e970b9b483ba5
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820965"
---
# <a name="member-overloading"></a>成員多載
成員多載表示在相同類型上建立兩個或多個成員，而這些成員只在參數的數目或類型不同，但具有相同的名稱。 例如，在下列範例中， `WriteLine` 方法會超載：

```csharp
public static class Console {
    public void WriteLine();
    public void WriteLine(string value);
    public void WriteLine(bool value);
    ...
}
```

 因為只有方法、函式和索引屬性可以有參數，所以只有這些成員可以多載。

 多載是改善可重複使用之程式庫的可用性、生產力和可讀性的最重要技術之一。 參數數目的多載可讓您提供更簡單版本的函式和方法。 參數類型上的多載可讓成員在一組選取的不同類型上執行相同的作業時，可以使用相同的成員名稱。

 ✔️請嘗試使用描述性參數名稱來表示較短的多載所使用的預設值。

 ❌ 避免在多載中任意改變參數名稱。 如果某個多載中的參數表示與另一個多載中的參數相同的輸入，則參數應具有相同的名稱。

 ❌ 避免在多載成員的參數順序中出現不一致的情況。 具有相同名稱的參數應該會出現在所有多載中的相同位置。

 如果) 需要擴充性，✔️只會進行最長的多載虛擬 (。 較短的多載應該只是呼叫較長的多載。

 ❌ 請勿使用或修飾詞來多載 `ref` `out` 成員。

 某些語言無法解析多載的呼叫，如下所示。 此外，這類多載通常會有完全不同的語法，但可能不應該是多載，而是兩個不同的方法。

 ❌ 沒有具有相同位置之參數的多載，以及具有不同語義的類似類型。

 ✔️允許 `null` 傳遞選擇性引數。

 ✔️確實使用成員多載，而不是使用預設引數來定義成員。

 預設引數不符合 CLS 標準。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [成員設計方針](member.md)
- [架構設計指導方針](index.md)
