---
title: "數值與比較運算子"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f77cb612468b401f6aa526e46cc7481d0b47d385
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="numeric-and-comparison-operators"></a>數值與比較運算子
除了下列幾點以外，在 Common Language Runtime (CLR) 中算術和比較運算子都會如預期運作：  
  
-   SQL 不支援浮點數值 (Floating-Point Number) 的模數運算子。  
  
-   SQL 不支援不檢查的算術。  
  
-   當您在無法於 SQL 中複寫因而不受支援的運算式中使用遞增和遞減運算子時，這些運算子會造成副作用。  
  
## <a name="supported-operators"></a>支援的運算子  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援下列運算子。  
  
-   基本算術運算子：  
  
    -   `+`  
  
    -   `-` (減法)  
  
    -   `*`  
  
    -   `/`  
  
    -   Visual Basic 整數除法 (`\`)  
  
    -   `%` (Visual Basic `Mod`)  
  
    -   `<<`  
  
    -   `>>`  
  
    -   `-` (一元否定運算)  
  
-   基本比較運算子：  
  
    -   Visual Basic `=` 和 C# `==`  
  
    -   Visual Basic `<>` 和 C# `!=`  
  
    -   Visual Basic `Is/IsNot`  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a>另請參閱  
 [資料型別和函式](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [C# 運算子](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [運算子](../../../../../visual-basic/language-reference/operators/index.md)
