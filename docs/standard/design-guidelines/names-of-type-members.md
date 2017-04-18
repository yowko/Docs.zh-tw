---
title: "型別成員名稱 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "事件 [.NET Framework] 名稱"
  - "方法 [.NET Framework] 名稱"
  - "類型成員"
  - "屬性 [.NET Framework] 名稱"
  - "欄位名稱"
  - "欄位名稱"
  - "名稱 [.NET Framework] 型別成員"
  - "輸入成員 [.NET Framework]"
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 型別成員名稱
型別由成員所組成︰ 方法、 屬性、 事件、 建構函式和欄位。 下列章節說明的指導方針命名型別成員。  
  
## 方法的名稱  
 方法是採取之動作的方法，因為設計指導方針會要求方法名稱是動詞或動詞片語。 依照此指導方針，也是用來區別屬性和型別名稱，也就是名詞或形容詞片語中的方法名稱。  
  
 **✓ 執行** 提供動詞或動詞片語的方法名稱。  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
  
```  
  
## 屬性名稱  
 不同於其他成員屬性應該指定名詞片語或形容詞的名稱。 這是因為屬性是指資料，以及屬性的名稱會反映。 PascalCasing 一律使用屬性名稱。  
  
 **✓ 執行** 屬性使用名詞、 名詞片語或形容詞。  
  
 **X 不** 沒有符合名稱的"Get"方法，如下列範例所示的屬性︰  
  
 `public string TextWriter { get {...} set {...} }`   
 `public string GetTextWriter(int value) { ... }`  
  
 此模式通常表示屬性其實應該是一種方法。  
  
 **✓ 執行** 集合屬性名稱與複數片語，描述的項目中的集合，而不使用單數片語，後面加上 「 清單 」 或 「 集合 」。  
  
 **✓ 執行** 與肯定的片語的布林值屬性 \(`CanSeek` 而不是 `CantSeek`\)。 （選擇性） 您也可以前面布林值屬性與 「 是 」，「 可以 」 或 「 有，」 但僅在將值加入。  
  
 **✓ 考慮** 為屬性提供其型別相同的名稱。  
  
 例如，下列屬性正確取得並設定列舉值，名稱為 `Color`, ，因此屬性的名稱是 `Color`:  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## 事件名稱  
 事件會參考進行的事情之一，或是已發生的某些動作。 因此，如同方法，事件會以動詞命令，來命名，而且動詞時態用來表示引發事件時的時間。  
  
 **✓ 執行** 命名事件的動詞或動詞片語。  
  
 範例包括 `Clicked`, ，`Painting`, ，`DroppedDown`, ，依此類推。  
  
 **✓ 執行** 命名事件的概念與之前和之後，使用目前和過去時態。  
  
 比方說，就會引發的視窗關閉之前關閉事件就會呼叫 `Closing`, ，並於視窗關閉之後會引發的其中一個就會呼叫 `Closed`。  
  
 **X 不** 使用 「 之前 」 或 「 之後 」 前置詞或 postfixes 來表示前置和後置的事件。 使用目前和過去時態如上所述。  
  
 **✓ 執行** 」 事件處理常式"後置詞命名事件處理常式 （委派做為事件的類型），如下列範例所示︰  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **✓ 執行** 使用名為兩個參數 `sender` 和 `e` 事件處理常式中。  
  
 傳送者參數表示引發事件的物件。 傳送者參數的型別通常是 `object`, ，即使可以採用更明確的類型。  
  
 **✓ 執行** 命名事件的 「 EventArgs"後置詞引數類別。  
  
## 欄位名稱  
 欄位命名指導方針適用於靜態公用和受保護的欄位。 內部和私用欄位未涵蓋的指導方針，和公用或受保護的執行個體欄位並不允許的 [成員設計方針](../../../docs/standard/design-guidelines/member.md)。  
  
 **✓ 執行** PascalCasing 用於欄位名稱。  
  
 **✓ 執行** 命名欄位使用名詞、 名詞片語或形容詞。  
  
 **X 不** 使用欄位名稱的前置詞。  
  
 例如，請勿 「 g\_ 」 或"s\_"來表示靜態欄位。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)