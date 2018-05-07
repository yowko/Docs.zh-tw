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
ms.openlocfilehash: 25fe93b63c518f54ee72300f26dfcb3f3ad21d76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="names-of-type-members"></a>類型成員名稱
類型由成員： 方法、 屬性、 事件、 建構函式和欄位。 下列章節說明的指導方針命名型別成員。  
  
## <a name="names-of-methods"></a>方法的名稱  
 因為方法都是採取之動作的方式，設計指導方針會需要方法名稱是動詞或動詞片語。 遵循這個指導方針也是用來區別屬性和型別名稱，也就是名詞或形容詞片語中的方法名稱。  
  
 **✓ 不要**提供動詞或動詞片語的方法名稱。  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a>屬性名稱  
 不同於其他成員屬性應該指定名詞片語或形容詞的名稱。 這是因為屬性參考到資料，以及屬性的名稱會反映。 PascalCasing 永遠用於屬性名稱。  
  
 **✓ 不要**命名屬性使用名詞、 名詞片語或形容詞。  
  
 **X 不**沒有符合的名稱 「 取得 」 方法，如下列範例所示的屬性：  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 此模式通常表示，屬性實際上應該是一種方法。  
  
 **✓ 不要**集合屬性名稱複數片語，描述的項目中的集合，而不是使用單數片語，後面接著 「 清單 」 或 「 集合 」。  
  
 **✓ 不要**命名肯定片語的布林值屬性 (`CanSeek`而不是`CantSeek`)。 （選擇性） 您也可以前面布林值屬性與 「 是 」，「 可以 」 或 「 沒有，」 但只在它將值。  
  
 **✓ 考慮**為屬性提供其型別相同的名稱。  
  
 例如，下列屬性正確取得並設定列舉值，名稱為`Color`，所以此屬性名為`Color`:  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a>事件的名稱  
 某些動作，其中一個已發生或發生的其中一個會參考事件。 因此，如同方法，事件會以動詞命令，來命名，而且動詞時態用來指示當引發事件的時間。  
  
 **✓ 不要**名稱具有動詞或動詞片語的事件。  
  
 範例包括`Clicked`， `Painting`， `DroppedDown`，依此類推。  
  
 **✓ 不要**提供事件名稱的概念與之前和之後，使用目前和過去時態。  
  
 例如，呼叫視窗關閉之前引發的關閉事件`Closing`，而且會呼叫一個視窗關閉後，就會引發`Closed`。  
  
 **X 不**使用 「 之前 」 或 「 之後 」 前置詞或 postfixes 表示前置和後置事件。 使用存在，以及過去時態，如上所述。  
  
 **✓ 不要**命名 」 事件處理常式 」 的後置詞，事件處理常式 （委派做為事件的類型），如下列範例所示：  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **✓ 不要**使用名為兩個參數`sender`和`e`事件處理常式中。  
  
 傳送者參數代表引發事件的物件。 傳送者參數的型別通常是`object`，即使可以採用更特定的類型。  
  
 **✓ 不要**命名事件引數"EventArgs"後置詞的類別。  
  
## <a name="names-of-fields"></a>欄位名稱  
 欄位命名指導方針適用於靜態公用和受保護的欄位。 內部及私人欄位未涵蓋的指導方針，而且公用或受保護的執行個體欄位不允許由[成員設計指導方針](../../../docs/standard/design-guidelines/member.md)。  
  
 **✓ 不要**PascalCasing 用於欄位名稱。  
  
 **✓ 不要**命名欄位使用名詞、 名詞片語或形容詞。  
  
 **X 不**使用欄位名稱的前置詞。  
  
 例如，請勿"g_"或"s_"，表示的靜態欄位。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)
