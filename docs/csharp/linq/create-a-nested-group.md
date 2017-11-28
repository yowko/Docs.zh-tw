---
title: "建立巢狀群組"
description: "如何建立巢狀群組。"
keywords: ".NET、.NET Core、C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 232aa46d975d7c338bbc776e3867f2e566601fde
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="create-a-nested-group"></a>建立巢狀群組

下列範例示範如何在 LINQ 查詢運算式中建立巢狀群組。 每個根據學年或年級層級建立的群組，接著會根據每個人的姓名進一步細分為群組。  
  
## <a name="example"></a>範例

 > [!NOTE]
 > 這個範例包含[查詢物件的集合](query-a-collection-of-objects.md)中範例程式碼中定義的物件參考。 

 [!code-csharp[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 請注意，需要有三個巢狀 `foreach` 迴圈，才能逐一查看巢狀群組的內部項目。  
  
## <a name="see-also"></a>請參閱  
 [LINQ 查詢運算式](index.md)
