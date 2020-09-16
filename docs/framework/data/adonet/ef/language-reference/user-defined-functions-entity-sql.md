---
title: 使用者定義函式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: ab18c3ec785ca3bba9f8b67fbb82fb4bb8244f4f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540650"
---
# <a name="user-defined-functions-entity-sql"></a>使用者定義函式 (Entity SQL)
Entity SQL 支援呼叫查詢中的使用者定義函式。 您可以定義這些函式內嵌在查詢中 (請參閱 [如何：呼叫使用者定義函數](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) 或做為概念模型的一部分 (參閱 [如何：在概念模型中定義自訂函數](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))) 。 概念模型函式在概念模型中的[Function](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl)元素的[DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl)元素中定義為 Entity SQL 命令。  
  
 Entity SQL 可讓您定義查詢命令自身中的函式。 [函數](function-entity-sql.md)運算子會定義內嵌函數。 您可以在單一命令中定義多個函式，只要函式的簽章是唯一的，這些函式可以有相同的函式名稱。 如需詳細資訊，請參閱 [Function Overload Resolution](function-overload-resolution-entity-sql.md)。  
  
## <a name="see-also"></a>請參閱

- [函式](functions-entity-sql.md)
