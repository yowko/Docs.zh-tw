---
title: 使用類型 'Object' 的引數時，請以 'FilePutObject' 代替 'FilePut'
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 3d793151905c61ee12eccdfdb5e9567a4924bb35
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725554"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a>使用類型 'Object' 的引數時，請以 'FilePutObject' 代替 'FilePut'
`FilePut` 方法包含類型 `Object`的引數。 `FilePutObject` 應該用於取代 `FilePut` ，以避免模稜兩可。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   將 `FilePut` 取代為 `FilePutObject`。  
  
-   請將 `Object` 引數轉換為更特定的類型。  
  
-   使用 `My.Computer.FileSystem` 物件中可用的功能。  
  
## <a name="see-also"></a>另請參閱

- [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
