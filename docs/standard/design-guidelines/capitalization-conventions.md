---
title: 大小寫慣例
description: 套用識別碼、複合字和一般詞彙的大小寫慣例。 瞭解在 .NET 中區分大小寫的運作方式。
ms.date: 10/22/2008
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
ms.openlocfilehash: 8df136fb57ad61ddfd87f4dec1f6490c63c3d977
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821524"
---
# <a name="capitalization-conventions"></a>大小寫慣例
本章中的指導方針會配置簡單的方法，以使用案例，在一致地套用時，讓類型、成員和參數的識別碼易於讀取。

## <a name="capitalization-rules-for-identifiers"></a>識別碼的大小寫規則
 若要區分識別碼中的單字，請將識別碼中每個單字的第一個字母大寫。 請勿使用底線來區分單字，或在識別碼中的任何位置區分單字。 有兩個適當的方式可將識別碼大寫，視識別碼的使用方式而定：

- PascalCasing

- >camelcasing

 PascalCasing 慣例（用於參數名稱以外的所有識別碼）會將每個字組的第一個字元設為大寫 (包括長度超過兩個字母的縮寫) ，如下列範例所示：

 `PropertyDescriptor`
 `HtmlTag`

 在兩個字母的縮寫中，這兩個字母都是大寫的特殊案例，如下列識別碼所示：

 `IOStream`

 >camelcasing 慣例（僅用於參數名稱）會將每個單字的第一個字元設為大寫，但不包括第一個單字，如下列範例所示。 如範例中所示，兩個字母的縮寫（開頭為 camel 大寫字母的識別碼）都是小寫。

 `propertyDescriptor`
 `ioStream`
 `htmlTag`

 ✔️將 PascalCasing 用於包含多個單字的所有公用成員、類型和命名空間名稱。

 ✔️請將 >camelcasing 用於參數名稱。

 下表描述不同類型之識別碼的大小寫規則。

|識別碼|大小寫|範例|
|----------------|------------|-------------|
|命名空間|帕斯卡|`namespace System.Security { ... }`|
|類型|帕斯卡|`public class StreamReader { ... }`|
|介面|帕斯卡|`public interface IEnumerable { ... }`|
|方法|帕斯卡|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|
|屬性|帕斯卡|`public class String {` <br />  `public int Length { get; }` <br /> `}`|
|事件|帕斯卡|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|
|欄位|帕斯卡|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|
|列舉值|帕斯卡|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|
|參數|Camel|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|

## <a name="capitalizing-compound-words-and-common-terms"></a>將複合單字和一般詞彙全部大寫
 大部分的複合詞匯都會被視為單一單字，以做為大小寫的用途。

 ❌ 請勿將所謂的封閉表單複合字中的每個單字全部大寫。

 這些是撰寫成單一單字的複合字，例如端點。 基於大小寫方針的目的，請將封閉形式的複合字視為單一單字。 使用目前的字典來判斷是否以封閉形式寫入複合字組。

|帕斯卡|Camel|否|
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
 可以在 CLR 上執行的語言不需要支援區分大小寫，但有一些可支援區分大小寫。 即使您的語言支援它，其他可能存取架構的語言也不會。 因此，可從外部存取的任何 Api 都不能單獨依賴大小寫來區別相同內容中的兩個名稱。

 ❌ 請勿假設所有程式設計語言都有區分大小寫。 但它們並不相等。 名稱不能單獨以大小寫不同。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [架構設計指導方針](index.md)
- [命名指導方針](naming-guidelines.md)
