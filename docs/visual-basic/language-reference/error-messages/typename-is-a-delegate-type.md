---
title: "'<typename>' 是委派類型"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 7056bbf2b4de26feba3bfbe0e02b3239311271c9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382168"
---
# <a name="typename-is-a-delegate-type"></a>'\<typename>' 是委派類型
' \<typename> ' 是委派類型。 委派結構只允許單一 AddressOf 運算式做為引數清單。 您通常可以使用 AddressOf 運算式，而不是委派結構。  
  
 `New`建立委派類別之實例的子句會提供不正確引數清單給委派的函式。  
  
 `AddressOf`建立新的委派實例時，您只能提供單一運算式。  
  
 如果您傳遞多個引數，或是傳遞不是有效運算式的單一引數，則不會將任何引數傳遞至委派的函式時，就會產生這個錯誤 `AddressOf` 。  
  
 **錯誤識別碼：** BC32008  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 在子句的 `AddressOf` 委派類別中，使用引數清單中的單一運算式 `New` 。  
  
## <a name="see-also"></a>另請參閱

- [New 運算子](../operators/new-operator.md)
- [AddressOf 運算子](../operators/addressof-operator.md)
- [委派](../../programming-guide/language-features/delegates/index.md)
- [如何：叫用委派方法](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
