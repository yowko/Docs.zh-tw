---
title: "使用者定義函式 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: df1b2a7c605134d57fcc21f9253373d4e0febb37
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="user-defined-functions-entity-sql"></a>使用者定義函式 (Entity SQL)
Entity SQL 支援呼叫查詢中的使用者定義函式。 您可以定義這些函式的內嵌查詢 (請參閱[How to: Call a User-Defined Function](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) 或做為概念模型的一部分 (請參閱[如何： 定義概念模型中的自訂函式](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f))。 概念模型函式定義在 Entity SQL 命令為[DefiningExpression](http://msdn.microsoft.com/en-us/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e)元素[函式](http://msdn.microsoft.com/en-us/dc3beca7-55cf-4977-8db0-5064cdbab134)概念模型中的項目。  
  
 Entity SQL 可讓您定義查詢命令自身中的函式。 [函式](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)運算子定義內嵌函式。 您可以在單一命令中定義多個函式，只要函式的簽章是唯一的，這些函式可以有相同的函式名稱。 如需詳細資訊，請參閱 [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)。  
  
## <a name="see-also"></a>請參閱  
 [函式](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
