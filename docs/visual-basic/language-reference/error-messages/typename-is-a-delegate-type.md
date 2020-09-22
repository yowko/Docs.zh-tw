---
title: "'<typename>' 是委派類型"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 4cc0a1221dcf65aa2a16fd7d82568c8544f27fdb
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875086"
---
# <a name="typename-is-a-delegate-type"></a>'\<typename>' 是委派類型

' \<typename> ' 是委派型別。 委派結構只允許單一 AddressOf 運算式作為引數清單。 您通常可以使用 AddressOf 運算式，而不是委派結構。  
  
 `New`建立委派類別實例的子句會提供不正確引數清單給委派的函式。  
  
 `AddressOf`建立新的委派實例時，您只能提供單一運算式。  
  
 如果您傳遞一個以上的引數，或傳遞的單一引數不是有效的運算式，就會產生這個錯誤 `AddressOf` 。  
  
 **錯誤識別碼：** BC32008  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 在 `AddressOf` 子句中使用委派類別的引數清單中的單一運算式 `New` 。  
  
## <a name="see-also"></a>另請參閱

- [New 運算子](../operators/new-operator.md)
- [AddressOf 運算子](../operators/addressof-operator.md)
- [委派](../../programming-guide/language-features/delegates/index.md)
- [如何：叫用委派方法](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
