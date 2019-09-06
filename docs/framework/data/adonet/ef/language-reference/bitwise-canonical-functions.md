---
title: 位元標準函式
ms.date: 03/30/2017
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
ms.openlocfilehash: 3c1f32acc7a035658198b807646c1ceb95dfed0b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251304"
---
# <a name="bitwise-canonical-functions"></a>位元標準函式
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 包含位元標準函式。  
  
## <a name="remarks"></a>備註  
 下表將顯示位元 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。 `Null` 如果`Null`提供輸入，則這些函式會傳回。 這些函式的傳回型別與引數型別相同。 引數必須屬於相同的型別 (如果函式接受多個引數的話)。 若要針對不同的型別執行位元運算，您必須明確轉型為相同的型別。  
  
|函數|說明|  
|--------------|-----------------|  
|`BitWiseAnd (` `value1` `,`  `value2` `)`|傳回 `value1` 和 `value2` 的位元結合，作為 `value1` 和 `value2` 的型別。<br /><br /> **引數**<br /><br /> `Byte`、 、`Int16`和`Int64`。 `Int32`<br /><br /> **範例**<br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|`BitWiseNot (` `value` `)`|傳回 `value` 的位元否定。<br /><br /> **引數**<br /><br /> `Byte`、 、`Int16`和`Int64`。 `Int32`<br /><br /> **範例**<br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|`BitWiseOr (` `value1` `,`  `value2` `)`|傳回 `value1` 和 `value2` 的位元分離，作為 `value1` 和 `value2` 的型別。<br /><br /> **引數**<br /><br /> `Byte` 、`Int16`和。`Int64` `Int32`<br /><br /> **範例**<br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|`BitWiseXor (` `value1` `,`  `value2` `)`|傳回 `value1` 和 `value2` 的位元排除分離，作為 `value1` 和 `value2` 的型別。<br /><br /> **引數**<br /><br /> `Byte` 、`Int16`和。`Int64` `Int32`<br /><br /> **範例**<br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a>另請參閱

- [標準函式](canonical-functions.md)
