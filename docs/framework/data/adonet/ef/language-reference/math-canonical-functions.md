---
title: 數學標準函式
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 0fc9f4942c3f76f139ab7e4400005f0bfe80204e
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46579332"
---
# <a name="math-canonical-functions"></a>數學標準函式

Entity SQL 包含下列的數學標準函式：
  
## <a name="absvalue"></a>Abs(value)

傳回 `value` 的絕對值。

**引數**

`Int16`， `Int32`， `Int64`， `Byte`， `Single`， `Double`，和`Decimal`。

**傳回值**

`value` 的類型。

**範例**

`Abs(-2)`

## <a name="ceilingvalue"></a>Ceiling(value)

傳回大於或等於 `value` 的最小整數。

**引數**

A `Single`， `Double`，和`Decimal`。

**傳回值**

`value` 的類型。

**範例**

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a>Floor(value)

傳回小於或等於 `value` 的最大整數。

**引數**

A `Single`， `Double`，和`Decimal`。

**傳回值**

`value` 的類型。

**範例**

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a>Power(值、指數)

傳回指定的 `value` 結果至指定的 `exponent`。

**引數**

|  |  |
|--|--|
|`value` | `Int32, Int64, Double`，或`Decimal`。 |
|`exponent` | `Int64`， `Double`，或`Decimal`。 |

**傳回值**

`value` 的類型。

**範例**

`Power(748.58,2)`

## <a name="roundvalue"></a>Round(value)

傳回 `value` 的整數部分，四捨五入成最接近的整數。

**引數**

A `Single`， `Double`，和`Decimal`。

**傳回值**

`value` 的類型。

**範例**

`Round(748.58)`

## <a name="roundvalue-digits"></a>Round(值、數字)

傳回 `value`，四捨五入至最接近的指定 `digits`。

**引數**

|  |  |
|--|--|
|`value`|`Double` 或 `Decimal`。|
|`digits`|`Int16` 或 `Int32`。|

**傳回值**

`value` 的類型。

**範例**

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a>Truncate(值、數字)

傳回 `value`，截斷至最接近的指定 `digits`。

**引數**

|  |  |
|--|--|
|`value`|`Double` 或 `Decimal`。|
|`digits`|`Int16` 或 `Int32`。|

**傳回值**

`value` 的類型。

**範例**

`Truncate(748.58,1)`  
  
 如果提供 `null` 輸入，這些函式會傳回 `null`。  
  
 Microsoft SQL Client Managed Provider 中提供了對等的功能。 如需詳細資訊，請參閱 <<c0> [ 適用於 Entity Framework 函式的 SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
