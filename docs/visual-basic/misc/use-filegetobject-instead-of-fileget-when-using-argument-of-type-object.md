---
title: 使用類型 'Object' 的引數時，請以 'FileGetObject' 代替 'FileGet'
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 318a0772a99aa86d9a4633e6021f77616a43fc7e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059401"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a>使用類型 'Object' 的引數時，請以 'FileGetObject' 代替 'FileGet'

`FileGet` 方法包含類型 `Object`的引數。 `FileGetObject` 應該用於取代 `FileGet` ，以避免模稜兩可。  
  
 請注意， `My.Computer.Filesystem` 所提供的功能比 `FileGet` 或 `FileGetObject`更容易使用和執行。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 將 `FileGet` 取代為 `FileGetObject`。  
  
2. 請將 `Object` 引數轉換為更特定的類型。  
  
## <a name="see-also"></a>另請參閱

- [我的電腦. 檔案系統](xref:Microsoft.VisualBasic.FileIO.FileSystem)
