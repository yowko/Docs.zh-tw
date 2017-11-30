---
title: "在類別建構函式中使用類別的「預設執行個體」，可能會導致無限遞迴呼叫。"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6a0c54c6e62f9bdc7fe510500a486461d26636d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>在類別建構函式中使用類別的「預設執行個體」，可能會導致無限遞迴呼叫。
類別的預設執行個體已用於類別的建構函式中。 這可能會導致無限遞迴呼叫 (也稱為無限迴圈)。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   從類別建構函式中移除預設執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [建構函式](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
