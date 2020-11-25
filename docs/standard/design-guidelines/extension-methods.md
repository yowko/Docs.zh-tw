---
title: 擴充方法
ms.date: 10/22/2008
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
ms.openlocfilehash: 02a421c9a4b73c779474a392e77104d4ccfbb109
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734708"
---
# <a name="extension-methods"></a>擴充方法

擴充方法是一種語言功能，可讓您使用實例方法呼叫語法來呼叫靜態方法。 這些方法必須至少要有一個參數，代表方法要操作的實例。

 定義這類擴充方法的類別稱為「贊助商」類別，必須宣告為靜態。 若要使用擴充方法，必須匯入定義贊助商類別的命名空間。

 ❌ 避免 frivolously 定義擴充方法，尤其是在您不擁有的類型上。

 如果您擁有類型的原始程式碼，請考慮改用一般實例方法。 如果您不是，而且想要新增方法，請務必小心。 使用擴充方法時，有可能會產生不是設計成具有這些方法的型別 Api。

 ✔️在下列任何情況下，請考慮使用擴充方法：

- 若要提供與介面每個執行相關的協助程式功能，請在核心介面中撰寫所述的功能。 這是因為實體執行無法以其他方式指派給介面。 例如， `LINQ to Objects` 運算子會實作為所有類型的擴充方法 <xref:System.Collections.Generic.IEnumerable%601> 。 因此，任何 `IEnumerable<>` 執行都會自動啟用 LINQ。

- 當實例方法會引入某個類型的相依性時，這類相依性會中斷相依性管理規則。 例如，從到的相依 <xref:System.String> 性 <xref:System.Uri?displayProperty=nameWithType> 可能不理想，因此從相依性管理的觀點來看，傳回 `String.ToUri()` 的實例方法會 `System.Uri` 是錯誤的設計。 傳回的靜態擴充方法會 `Uri.ToUri(this string str)` `System.Uri` 是更好的設計。

 ❌ 避免在上定義擴充方法 <xref:System.Object?displayProperty=nameWithType> 。

 VB 使用者將無法在使用擴充方法語法的物件參考上呼叫這類方法。 VB 不支援呼叫這類方法，因為在 VB 中，將參考宣告為物件時，會將其上的所有方法調用強制為晚期繫結 (實際呼叫的成員是在執行時間) 所決定，而擴充方法的系結則是在編譯時期 (早期繫結) 所決定。

 請注意，此指導方針適用于存在相同系結行為的其他語言，或不支援擴充方法的情況。

 ❌ 除非將擴充方法加入介面或相依性管理的方法，否則請勿將擴充方法放在與擴充類型相同的命名空間中。

 ❌ 請避免使用相同的簽章來定義兩個或多個擴充方法，即使它們位於不同的命名空間中。

 如果類型是介面，且擴充方法的目的是要用於大部分或所有案例中，✔️請考慮在與擴充類型相同的命名空間中定義擴充方法。

 ❌ 請勿定義擴充方法，以在通常與其他功能相關聯的命名空間中執行功能。 相反地，請在與其所屬功能相關聯的命名空間中定義它們。

 ❌ 避免對延伸方法專屬的命名空間進行泛型命名， (例如「延伸模組」 ) 。 請改用描述性名稱 (例如「路由」 ) 。

 *部分 &copy; 2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>另請參閱

- [成員設計方針](member.md)
- [架構設計指導方針](index.md)
