---
title: 使用類型 'Object' 的引數時，請以 'FileGetObject' 代替 'FileGet'
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: fdad64a4b35aa792c996d25a9fd72a9ce1126fbd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306920"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a>使用類型 'Object' 的引數時，請以 'FileGetObject' 代替 'FileGet'
`FileGet` 方法包含類型 `Object`的引數。 `FileGetObject` 應該用於取代 `FileGet` ，以避免模稜兩可。  
  
 請注意， `My.Computer.Filesystem` 所提供的功能比 `FileGet` 或 `FileGetObject`更容易使用和執行。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 將 `FileGet` 取代為 `FileGetObject`。  
  
2. 請將 `Object` 引數轉換為更特定的類型。  
  
## <a name="see-also"></a>另請參閱

- [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
