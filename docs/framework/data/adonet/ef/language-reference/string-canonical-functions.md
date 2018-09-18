---
title: 字串標準函式
ms.date: 03/30/2017
ms.assetid: 5e2cbebd-5df3-47c7-b0e2-49a17ab22bfb
ms.openlocfilehash: d4758f8325b99bc4bd91575dd774d2dabde1f925
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46009547"
---
# <a name="string-canonical-functions"></a>字串標準函式
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 包含字串標準函式。  
  
## <a name="remarks"></a>備註  
 下表將顯示字串 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。  
  
|函式|描述|  
|--------------|-----------------|  
|`Concat(string1, string2)`|傳回包含附加至 `string2` 之 `string1` 的字串。<br /><br /> **引數**<br /><br /> `string1`：`string2` 附加至的字串。<br /><br /> `string2`：附加至 `string1` 的字串。<br /><br /> **傳回值**<br /><br /> `String`。 如果傳回值字串的長度超過允許的最大長度，就會發生錯誤。<br /><br /> **範例**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Contains(string, target)`|如果 `true` 包含在 `target` 之中，傳回`string`。<br /><br /> **引數**<br /><br /> `string`：用來搜尋的字串。<br /><br /> `target`：搜尋的目標字串。<br /><br /> **傳回值**<br /><br /> 如果 `true` 包含在 `target` 中，則為 `string`，否則為 `false`。<br /><br /> **範例**<br /><br /> `-- The following example returns true.`<br /><br /> `Contains('abc', 'bc')`|  
|`EndsWith(string, target)`|如果 `true` 是以 `target` 為結尾，傳回 `string`。<br /><br /> **引數**<br /><br /> `string`：用來搜尋的字串。<br /><br /> `target`：搜尋位於 `string` 結尾處的目標字串。<br /><br /> **傳回值**<br /><br /> 如果 `True` 是以 `string` 為結尾，則為 `target`，否則為 `false`。<br /><br /> **範例**<br /><br /> `-- The following example returns true.`<br /><br /> `EndsWith('abc', 'bc')` **注意︰** 如果您使用 SQL Server 資料提供者，此函數會傳回`false`如果要將字串儲存在固定的長度字串資料行和`target`是常數。 在這個情況下，會搜尋到整個字串，包括任何填補的後端空格。 可能的解決方法是修剪固定長度字串中的資料，如以下範例所示：`EndsWith(TRIM(string), target)`|  
|`IndexOf(target, string)`|傳回 `target` 在 `string` 內部的位置，或 0 (如果找不到的話)。 傳回 1 表示 `string` 的開頭。 索引編號會從 1 開始。<br /><br /> **引數**<br /><br /> `target`：搜尋的目標字串。<br /><br /> `string`：用來搜尋的字串。<br /><br /> **傳回值**<br /><br /> `Int32`。<br /><br /> **範例**<br /><br /> `-- The following example returns 4.`<br /><br /> `IndexOf('xyz', 'abcxyz')`|  
|`Left(string, length)`|從 `length` 的左側傳回前 `string` 個字元。 如果 `string` 的長度小於 `length`，就會傳回整個字串。<br /><br /> **引數**<br /><br /> `string`：`String`。<br /><br /> `length`：`Int16`、`Int32`、`Int64` 或 `Byte`。 `length` 不得小於零。<br /><br /> **傳回值**<br /><br /> `String`。<br /><br /> **範例**<br /><br /> `-- The following example returns abc.`<br /><br /> `Left('abcxyz', 3)`|  
|`Length(string)`|傳回字串的 (`Int32`) 長度 (以字元為單位)。<br /><br /> **引數**<br /><br /> `string`：`String`。<br /><br /> **傳回值**<br /><br /> `Int32`。<br /><br /> **範例**<br /><br /> `-- The following example returns 6.`<br /><br /> `Legth('abcxyz')`|  
|`LTrim(string)`|傳回`string`不含任何前置空白字元。<br /><br /> **引數**<br /><br /> `String`。<br /><br /> **傳回值**<br /><br /> `String`。<br /><br /> **範例**<br /><br /> `-- The following example returns abc.`<br /><br /> `LTrim('   abc')`|  
|`Replace(string1, string2, string3)`|傳回 `string1`，並將 `string2` 的所有相符項目取代成 `string3`。<br /><br /> **引數**<br /><br /> `String`。<br /><br /> **傳回值**<br /><br /> `String`。<br /><br /> **範例**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Reverse(string)`|使用反向字元的順序傳回 `string`。<br /><br /> **引數**<br /><br /> `String`。<br /><br /> **傳回值**<br /><br /> `String`。<br /><br /> **範例**<br /><br /> `-- The following example returns dcba.`<br /><br /> `Reverse('abcd')`|  
|`Right(string, length)`|傳回最後`length`字元`string`。 如果 `string` 的長度小於 `length`，就會傳回整個字串。<br /><br /> **引數**<br /><br /> `string`：`String`。<br /><br /> `length`：`Int16`、`Int32`、`Int64` 或 `Byte`。 `length` 不得小於零。<br /><br /> **傳回值**<br /><br /> `String`。<br /><br /> **範例**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Right('abcxyz', 3)`|  
|`RTrim(string)`|傳回`string`不含任何結尾空白字元。<br /><br /> **引數**<br /><br /> `String`。<br /><br /> **傳回值**<br /><br /> `String`。|  
|`Substring(string, start, length)`|從位置 `start` 開始傳回字串的子字串，而且長度為 `length` 個字元。 start 為 1 是表示字串的第一個字元。 索引編號會從 1 開始。<br /><br /> **引數**<br /><br /> `string`：`String`。<br /><br /> `start`：`Int16`、`Int32`、`Int64` 和 `Byte`。 `start` 不得小於一。<br /><br /> `length`：`Int16`、`Int32`、`Int64` 和 `Byte`。 `length` 不得小於零。<br /><br /> **傳回值**<br /><br /> `String`。<br /><br /> **範例**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Substring('abcxyz', 4, 3)`|  
|`StartsWith(string, target)`|如果 `true` 是以 `string` 為開頭，傳回 `target`。<br /><br /> **引數**<br /><br /> `string`：用來搜尋的字串。<br /><br /> `target`：搜尋位於 `string` 開頭處的目標字串。<br /><br /> **傳回值**<br /><br /> 如果 `True` 是以 `string` 為開頭，則為 `target`，否則為 `false`。<br /><br /> **範例**<br /><br /> `-- The following example returns true.`<br /><br /> `StartsWith('abc', 'ab')`|  
|`ToLower(string)`|傳回將大寫字元轉換成小寫的 `string`。<br /><br /> **引數**<br /><br /> `String`。<br /><br /> **傳回值**<br /><br /> `String`。<br /><br /> **範例**<br /><br /> `-- The following example returns abc.`<br /><br /> `ToLower('ABC')`|  
|`ToUpper(string)`|傳回將小寫字元轉換成大寫的 `string`。<br /><br /> **引數**<br /><br /> `String`。<br /><br /> **傳回值**<br /><br /> `String`。<br /><br /> **範例**<br /><br /> `-- The following example returns ABC.`<br /><br /> `ToUpper('abc')`|  
|`Trim(string)`|傳回`string`不含任何開頭和尾端空白字元。<br /><br /> **引數**<br /><br /> `String`。<br /><br /> **傳回值**<br /><br /> `String`。<br /><br /> **範例**<br /><br /> `-- The following example returns abc.`<br /><br /> `Trim('      abc   ')`|  
  
 如果提供 `null` 輸入，這些函式會傳回 `null`。  
  
 Microsoft SQL Client Managed Provider 中提供了對等的功能。 如需詳細資訊，請參閱 <<c0> [ 適用於 Entity Framework 函式的 SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
