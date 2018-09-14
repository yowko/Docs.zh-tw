---
title: 類型成員名稱
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0541f100f208543c796de7238e68ea6f90c7b299
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45588380"
---
# <a name="names-of-type-members"></a>類型成員名稱
類型由成員組成：方法、屬性、事件、建構函式及欄位。 下列各節會描述為類型成員命名的方針。  
  
## <a name="names-of-methods"></a>方法的名稱  
 因為方法是採取動作的手段，所以設計方針會要求方法名稱為動詞或動詞片語。 遵循此方針也能用來區別方法名稱與屬性和類型名稱，後兩者為名詞或形容詞。  
  
 **✓ DO** 提供是動詞或動詞片語的方法名稱。  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a>屬性的名稱  
 不同於其他成員，屬性應有名詞片語或形容詞名稱。 這是因為屬性會參考資料，而屬性的名稱則會反映這點。 PascalCasing 總是會用作屬性名稱。  
  
 **✓ DO** 使用名詞、名詞片語或形容詞來命名屬性。  
  
 **X DO NOT** 使屬性符合 "Get" 方法的名稱，如以下範例所示：  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 此模式通常表示屬性應該真的是方法。  
  
 **✓ DO** 以單數片語命名集合屬性，描述集合中的項目而非使用後面接著 "List" 或 "Collection" 的單數片語。  
  
 **✓ DO** 以肯定片語 (`CanSeek` 而非 `CantSeek`) 命名布林值屬性。 此外，您也可以使用 "Is,"、"Can," 或 "Has," 作為布林值屬性的首碼，但僅限於新增值的情況。  
  
 **✓ CONSIDER** 為屬性提供與其類型相同的名稱。  
  
 例如，下列屬性正確地取得並設定了名為 `Color` 的數值，所以屬性名稱即為 `Color`：  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a>事件的名稱  
 事件一律會參考某些動作，不論該動作正在發生或已發生。 因此，如同方法一般，事件應以動詞為名，且應使用動詞時態來指出事件發生的時間。  
  
 **✓ DO** 以動詞或動詞片語命名事件。  
  
 範例包括 `Clicked`、`Painting`、`DroppedDown` 等等。  
  
 **✓ DO** 使用現在和過去式，來為事件賦予具有現在和之後概念的名稱。  
  
 例如，在視窗關閉前發生的關閉事件會稱作 `Closing`，而在視窗關閉後發生的事件則稱作 `Closed`。  
  
 **X DO NOT** 使用 "Before" 或 "After" 首碼與尾碼來表示之前和之後的事件。 使用如同敘述的現在與過去時態。  
  
 **✓ DO** 以 "EventHandler" 尾碼來命名事件處理常式 (用作事件類型的委派)，如下列範例中所示：  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **✓ DO** 在事件處理常式中使用名為 `sender` 和 `e` 的兩個參數。  
  
 傳送者參數代表引發事件的物件。 傳送者參數的類型通常為 `object`，即使可採用更明確的類型時也一樣。  
  
 **✓ DO** 以 "EventArgs" 尾碼命名事件引數類別。  
  
## <a name="names-of-fields"></a>欄位的名稱  
 欄位命名方針適用於靜態公開和保護的欄位。 方針並未涵蓋內部與私人的欄位，且[成員設計方針](../../../docs/standard/design-guidelines/member.md)並不允許公開或保護的執行個體欄位。  
  
 **✓ DO** 在欄位名稱中使用 PascalCasing。  
  
 **✓ DO** 使用名詞、名詞片語或形容詞來命名欄位。  
  
 **X DO NOT** 為欄位名稱使用首碼。  
  
 例如，不要使用 "g_" 或 "s_" 來表示靜態欄位。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
- [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)
