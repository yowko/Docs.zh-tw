---
title: 使用類型 'Object' 的引數時，請以 'FileGetObject' 代替 'FileGet'
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: ddbe187ed1210d238448a5ff3feaee18beea1def
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2018
ms.locfileid: "53768007"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a>使用類型 'Object' 的引數時，請以 'FileGetObject' 代替 'FileGet'
`FileGet` 方法包含類型 `Object` 的引數。 `FileGetObject` 應該用於取代 `FileGet` ，以避免模稜兩可。  
  
 請注意， `My.Computer.Filesystem` 所提供的功能比 `FileGet` 或 `FileGetObject`更容易使用和執行。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  將 `FileGet` 取代為 `FileGetObject`。  
  
2.  請將 `Object` 引數轉換為更特定的類型。  
  
## <a name="see-also"></a>另請參閱  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
