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
ms.openlocfilehash: 7ef7913a2601c3a791cb028b4074ce37b9e9421b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575280"
---
# <a name="capitalization-conventions"></a>大小寫慣例
簡單的方法，使用這個章節配置中的指導方針情況下，當套用一致的方式，請識別項的類型、 成員和參數容易閱讀。  
  
## <a name="capitalization-rules-for-identifiers"></a>識別項的大小寫規則  
 若要區分識別項中的文字，將變成大寫識別項中的每個單字的第一個的字母。 請勿使用底線來區分文字，或該項目的，識別項中的任何位置。 有兩個適當的方法可以改為大寫的識別項，根據所使用的識別項：  
  
-   PascalCasing  
  
-   camelCasing  
  
 PascalCasing 慣例使用於所有的識別項，除了參數名稱轉換成大寫字母 （包括透過長度的兩個字母的首字母縮略字） 的每個單字的第一個字元，如下列範例所示：  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 特殊案例對兩個字母縮略字，這兩個字母都大寫，如下列的識別項中所示：  
  
 `IOStream`  
  
 CamelCasing 慣例，只能用於參數名稱轉換成大寫字母的第一個字，除了每個單字的第一個字元，如下列範例所示。 此範例也示範，因為開始依照 camel 命名法的大小寫慣例的識別項的兩個字母縮略字都是小寫。  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **✓ 請** 為所有由多個單字所組成的公用成員、 類型和命名空間名稱使用 PascalCasing。  
  
 **✓ 請** 為參數名稱使用 camelCasing。    
  
 下表說明不同類型的識別項的大小寫規則。  
  
|識別項|大小寫|範例|  
|----------------|------------|-------------|  
|命名空間|依照 pascal 命名法|`namespace System.Security { ... }`|  
|類型|依照 pascal 命名法|`public class StreamReader { ... }`|  
|介面|依照 pascal 命名法|`public interface IEnumerable { ... }`|  
|方法|依照 pascal 命名法|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|屬性|依照 pascal 命名法|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|Event - 事件|依照 pascal 命名法|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|欄位|依照 pascal 命名法|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|列舉值|依照 pascal 命名法|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|參數|依照 camel 命名法|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>大寫的複合字和一般詞彙  
 大部分的複合詞彙會被視為基於大小寫的單字。  
  
 **X 不**所謂的封閉式複合字組中的每個字大寫。  
  
 這些是寫成單一的文字，例如端點的複合字。 大小寫的指導方針，以便將關閉表單的複合字視為單一文字。 您可以使用目前的字典來判斷複合字以關閉表單。  
  
|依照 pascal 命名法|依照 camel 命名法|not|  
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
 可以在 CLR 執行的語言不需要支援區分大小寫，雖然有些執行。 即使您的語言支援，就可能存取您的架構的其他語言則否。 任何應用程式開發介面可外部存取，因此，不能依賴來區別兩個名稱相同的內容中的案例。  
  
 **X 不**假設所有的程式語言不區分大小寫。 但它們並不相等。 名稱不能單獨的大小寫不同。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)
