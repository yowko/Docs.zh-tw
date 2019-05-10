---
title: 在類別建構函式中使用類別的「預設執行個體」，可能會導致無限遞迴呼叫。
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: 1cad1e3cf3943e945d519aee061a877c91684b4a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623475"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>在類別建構函式中使用類別的「預設執行個體」，可能會導致無限遞迴呼叫。
類別的預設執行個體已用於類別的建構函式中。 這可能會導致無限遞迴呼叫 (也稱為無限迴圈)。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 從類別建構函式中移除預設執行個體。  
  
## <a name="see-also"></a>另請參閱

- [建構函式](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
