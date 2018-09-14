---
title: 大小寫慣例
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 070fc69728c2cb38e465dab9f6f591a77a857531
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45568458"
---
# <a name="capitalization-conventions"></a>大小寫慣例
簡單的方法，使用這一章配置中的指導方針情況下，當套用一致的方式，請識別項型別、 成員和參數容易閱讀。  
  
## <a name="capitalization-rules-for-identifiers"></a>識別項的大小寫規則  
 若要區分識別項中的文字，利用識別項中的每個單字的第一個字母。 請勿使用底線來區分文字，或就此而言，在識別項中任何位置。 有兩個適當的方法，可以改為大寫識別碼，根據所使用的識別項：  
  
-   PascalCasing  
  
-   camelCasing  
  
 參數名稱除外的所有識別項所使用的 PascalCasing 慣例轉換成大寫字母 （包括透過長度的兩個字母的縮寫） 的每個字的第一個字元，如下列範例所示：  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 特殊案例是進行中這兩個字母大寫，兩個字母縮寫，下列識別碼中所示：  
  
 `IOStream`  
  
 CamelCasing 慣例，參數名稱，僅用於轉換成大寫字母的第一個字，除了每個單字的第一個字元，如下列範例所示。 因為此範例也示範，開始使用依照 camel 命名法大小寫的識別項的兩個字母縮略字都是小寫。  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **✓ 請** 為所有由多個單字所組成的公用成員、 類型和命名空間名稱使用 PascalCasing。  
  
 **✓ 請** 為參數名稱使用 camelCasing。    
  
 下表描述不同類型的識別項的大小寫規則。  
  
|識別項|大小寫|範例|  
|----------------|------------|-------------|  
|命名空間|Pascal 命名法|`namespace System.Security { ... }`|  
|類型|Pascal 命名法|`public class StreamReader { ... }`|  
|介面|Pascal 命名法|`public interface IEnumerable { ... }`|  
|方法|Pascal 命名法|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|屬性|Pascal 命名法|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|Event - 事件|Pascal 命名法|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|欄位|Pascal 命名法|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|列舉值|Pascal 命名法|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|參數|依照 camel 命名法|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>大寫的複合字和一般詞彙  
 大部分的複合詞彙會被視為單一字詞大小寫的目的。  
  
 **X DO NOT** 所謂的封閉式複合字組中的每個字大寫。  
  
 這些是寫成單字，例如端點的複合字。 大小寫的指導方針，以將關閉表單的複合字視為單一的文字。 使用目前的字典來判斷複合字以關閉表單。  
  
|Pascal 命名法|依照 camel 命名法|not|  
|------------|-----------|---------|  
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
  
## <a name="case-sensitivity"></a>區分大小寫  
 雖然有些可以在 CLR 執行的語言不需要支援區分大小寫。 即使您的語言支援，可能會存取您的架構的其他語言則否。 任何 Api，從外部存取，因此，不能依賴來區別兩個名稱相同的內容中的案例。  
  
 **X DO NOT** 假設所有的程式語言不區分大小寫。 但它們並不相等。 名稱不能單獨的大小寫不同。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
- [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)
