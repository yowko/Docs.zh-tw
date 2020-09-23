---
title: 編碼不能設定為 Nothing。
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 0356098ca3fb41804ea396b0ff792cf2990b3340
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077536"
---
# <a name="encoding-cannot-be-set-to-nothing"></a>編碼不能設定為 Nothing。

讀取或寫入檔案的嘗試失敗，因為參數 `encoding` 已設定為 `Nothing` ，但需要有效的值。  
  
 <xref:System.Text.Encoding> 用來判斷在寫入檔案時要使用的編碼方式。 預設值為 UTF-8。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請為 `encoding` 參數提供有效的值。  
  
## <a name="see-also"></a>另請參閱

- [檔案編碼方式](../developing-apps/programming/drives-directories-files/file-encodings.md)
- [從檔案讀取](../developing-apps/programming/drives-directories-files/reading-from-files.md)
- [寫入檔案](../developing-apps/programming/drives-directories-files/writing-to-files.md)
- [My.user. ReadAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [My.user. WriteAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
