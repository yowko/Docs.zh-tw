---
title: "大小寫慣例 | Microsoft Docs"
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
  - "依照 camel 命名法的大小寫慣例名稱 [.NET Framework]"
  - "類別庫設計方針 [.NET Framework] 的大小寫"
  - "Pascal 命名法的大小寫慣例名稱 [.NET Framework]"
  - "區分大小寫慣例"
  - "名稱 [.NET Framework] 的大小寫"
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# 大小寫慣例
簡單的方法，使用這一章配置中的指導方針情況下，當套用一致的方式，請識別項型別、 成員和參數容易閱讀。  
  
## 識別項的大小寫規則  
 若要區分識別項中的單字，充分利用每個單字的識別項的第一個字母。 請勿使用底線來區分文字，或就此而言，識別項中的任何位置。 有兩個適當的方法，可以改為大寫的識別項，根據所使用的識別項︰  
  
-   PascalCasing  
  
-   camelCasing  
  
 PascalCasing 慣例使用於所有的識別項，除了參數名稱轉換成大寫字母每個字 （包括透過長度的兩個字母的首字母縮略字），第一個的字元，如下列範例所示︰  
  
 `PropertyDescriptor`   
 `HtmlTag`  
  
 特殊案例中這兩個字母大寫，兩個字母縮略字的由下列的識別項中所示︰  
  
 `IOStream`  
  
 CamelCasing 慣例，參數名稱僅用於轉換成大寫字母的第一個字，除了每個單字的第一個字元，如下列範例所示。 因為此範例也示範，開始依照 camel 命名法的大小寫慣例的識別項的兩個字母縮寫字都是小寫。  
  
 `propertyDescriptor`   
 `ioStream`   
 `htmlTag`  
  
 **✓ 執行** PascalCasing 所有公用成員、 類型和命名空間名稱使用多個單字所組成。  
  
 **✓ 執行** camelCasing 用於參數名稱。  
  
 下表描述不同類型的識別項的大小寫規則。  
  
|識別項|大小寫|範例|  
|---------|---------|--------|  
|命名空間|Pascal 命名法|`namespace System.Security { ... }`|  
|類型|Pascal 命名法|`public class StreamReader { ... }`|  
|介面|Pascal 命名法|`public interface IEnumerable { ... }`|  
|方法|Pascal 命名法|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|屬性|Pascal 命名法|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|事件|Pascal 命名法|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|欄位|Pascal 命名法|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|列舉值|Pascal 命名法|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|參數|依照 camel 命名法|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## 大寫複合字和一般詞彙  
 大部分的複合詞彙會被視為單一文字大小寫的目的。  
  
 **X 不** 充分利用每個單字的所謂封閉式複合字。  
  
 這些是寫成單一的文字，例如端點的複合字。 大小寫的指導方針，以將封閉式複合字視為單一文字。 您可以使用目前的字典來決定的複合字以關閉表單。  
  
|Pascal 命名法|依照 camel 命名法|不|  
|----------------|------------------|-------|  
|`BitFlag`|`bitFlag`|`Bitflag`|  
|`Callback`|`callback`|`CallBack`|  
|`Canceled`|`canceled`|`Cancelled`|  
|`DoNot`|`doNot`|`Don't`|  
|`Email`|`email`|`EMail`|  
|`Endpoint`|`endpoint`|`EndPoint`|  
|`FileName`|`fileName`|`Filename`|  
|`Gridline`|`gridline`|`GridLine`|  
|`Hashtable`|`hashtable`|`HashTable`|  
|`Id`|`id`|`ID`|  
|`Indexes`|`indexes`|`Indices`|  
|`LogOff`|`logOff`|`LogOut`|  
|`LogOn`|`logOn`|`LogIn`|  
|`Metadata`|`metadata`|`MetaData, metaData`|  
|`Multipanel`|`multipanel`|`MultiPanel`|  
|`Multiview`|`multiview`|`MultiView`|  
|`Namespace`|`namespace`|`NameSpace`|  
|`Ok`|`ok`|`OK`|  
|`Pi`|`pi`|`PI`|  
|`Placeholder`|`placeholder`|`PlaceHolder`|  
|`SignIn`|`signIn`|`SignOn`|  
|`SignOut`|`signOut`|`SignOff`|  
|`UserName`|`userName`|`Username`|  
|`WhiteSpace`|`whiteSpace`|`Whitespace`|  
|`Writable`|`writable`|`Writeable`|  
  
## 區分大小寫  
 可以在 CLR 執行的語言不支援所需區分大小寫，雖然有些人是如此。 即使您的語言支援，可能需要存取您的架構的其他語言則否。 因此，外部存取，任何 Api 不能單獨用來區別兩個名稱相同的內容中的案例。  
  
 **X 不** 假設所有的程式語言不區分大小寫。 它們不是。 名稱不能單獨的大小寫不同。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)