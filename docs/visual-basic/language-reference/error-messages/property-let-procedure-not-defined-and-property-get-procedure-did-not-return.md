---
title: "未定義屬性 let 的程序，而屬性 get 的程序並未傳回物件"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b043ca698a9c90afd41de90c7dbc5879ae7de623
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a>未定義屬性 let 的程序，而屬性 get 的程序並未傳回物件
特定的屬性、 方法和作業只能套用至`Collection`物件。 您指定的作業或專屬於集合的屬性，但物件不是集合。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查拼字的物件或屬性名稱，或確認物件是`Collection`物件。  
  
2.  查看`Add`方法用來將物件加入至集合，以便能確定語法是否正確，以及任何識別項的拼字是否正確。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Collection>
