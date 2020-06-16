---
title: 大小寫慣例
description: 針對識別碼、複合字和共同詞彙套用大小寫慣例。 瞭解在 .NET 中區分大小寫的運作方式。
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
ms.openlocfilehash: 4903dc587d84ef36bfaa641cfbda59484266c23c
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767789"
---
# <a name="capitalization-conventions"></a>大小寫慣例
本章中的指導方針會配置一個簡單的方法，以便在一致地套用時，讓型別、成員和參數的識別碼易於閱讀。

## <a name="capitalization-rules-for-identifiers"></a>識別碼的大小寫規則
 若要區分識別碼中的單字，請將識別碼中每個單字的第一個字母大寫。 請不要使用底線來區別單字，或在識別碼中的任何位置區分。 有兩個適當的方式可將識別碼大寫，視使用識別碼而定：

- PascalCasing

- camelCasing

 PascalCasing 慣例，用於參數名稱以外的所有識別碼，會將每個字組的第一個字元（包含長度超過兩個字母的縮寫）設為大寫，如下列範例所示：

 `PropertyDescriptor`
 `HtmlTag`

 特殊案例是針對兩個字母的縮寫，其中兩個字母都是大寫，如下列識別碼所示：

 `IOStream`

 CamelCasing 慣例僅用於參數名稱，會將每個字組的第一個字元設為大寫，但第一個單字除外，如下列範例所示。 如範例所示，開始使用 camel 大小寫識別碼的兩個字母縮略字，兩者都是小寫。

 `propertyDescriptor`
 `ioStream`
 `htmlTag`

 ✔️對於所有包含多個單字的公用成員、類型和命名空間名稱，請使用 PascalCasing。

 ✔️請對參數名稱使用 camelCasing。

 下表描述不同識別碼類型的大小寫規則。

|識別碼|大小寫|範例|
|----------------|------------|-------------|
|命名空間|Pascal|`namespace System.Security { ... }`|
|類型|Pascal|`public class StreamReader { ... }`|
|介面|Pascal|`public interface IEnumerable { ... }`|
|方法|Pascal|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|
|屬性|Pascal|`public class String {` <br />  `public int Length { get; }` <br /> `}`|
|事件|Pascal|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|
|欄位|Pascal|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|
|列舉值|Pascal|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|
|參數|Camel|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|

## <a name="capitalizing-compound-words-and-common-terms"></a>將複合字和共同詞彙大寫
 大部分的複合詞匯會視為大寫用途的單一單字。

 ❌請不要將所謂的封閉表單複合單字中的每個字大寫。

 這些是以單一單字撰寫的複合字組，例如端點。 基於大小寫方針的目的，請將封閉形式的複合字視為單一單字。 使用目前的字典來判斷複合字是否以已關閉的形式寫入。

|Pascal|Camel|Not|
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
 可以在 CLR 上執行的語言並不需要支援區分大小寫，雖然有些也是如此。 即使您的語言支援它，其他可能存取您架構的語言也不會。 因此，可從外部存取的任何 Api 都不能單獨依賴大小寫來區別相同內容中的兩個名稱。

 ❌請勿假設所有程式設計語言都區分大小寫。 但它們並不相等。 名稱不能單獨以大小寫不同。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [架構設計方針](index.md)
- [命名方針](naming-guidelines.md)
