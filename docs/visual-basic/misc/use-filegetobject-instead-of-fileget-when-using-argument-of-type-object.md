---
title: 使用類型 'Object' 的引數時，請以 'FileGetObject' 代替 'FileGet'
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 60eaabc686070aced908116728f06d4e82b5cecb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723390"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a>使用類型 'Object' 的引數時，請以 'FileGetObject' 代替 'FileGet'
`FileGet` 方法包含類型 `Object`的引數。 `FileGetObject` 應該用於取代 `FileGet` ，以避免模稜兩可。  
  
 請注意， `My.Computer.Filesystem` 所提供的功能比 `FileGet` 或 `FileGetObject`更容易使用和執行。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  將 `FileGet` 取代為 `FileGetObject`。  
  
2.  請將 `Object` 引數轉換為更特定的類型。  
  
## <a name="see-also"></a>另請參閱

- [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
