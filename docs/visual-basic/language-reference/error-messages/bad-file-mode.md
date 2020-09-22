---
title: 不正確的檔案模式
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 99b84902ddf032f2ecb6e26400e200bea862dfdf
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875155"
---
# <a name="bad-file-mode"></a>不正確的檔案模式

用於操作檔案內容的語句，必須適合用來開啟檔案的模式。 可能原因包括：  
  
- `FilePutObject`或 `FileGetObject` 語句會指定順序檔案。  
  
- `Print`語句會指定針對或以外的存取模式開啟的檔案 `Output` `Append` 。  
  
- `Input`語句會指定為存取模式開啟的檔案，而非`Input`  
  
- 嘗試寫入至唯讀檔案。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請確定 `FilePutObject` 並 `FileGetObject` 只參照開啟或存取的檔案 `Random` `Binary` 。  
  
- 請確定 `Print` 針對 `Output` 或存取模式指定開啟的檔案 `Append` 。 如果沒有，請使用不同的語句將資料放入檔案中，或在適當的模式中重新開啟檔案。  
  
- 請確定 `Input` 指定開啟的檔案 `Input` 。 如果沒有，請使用不同的語句將資料放入檔案中，或在適當模式中重新開啟檔案。  
  
- 如果您要寫入至唯讀檔案，請變更檔案的讀取/寫入狀態，或不要嘗試寫入檔案。  
  
- 使用 `My.Computer.FileSystem` 物件中可用的功能。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileSystem>
- [疑難排解：讀取和寫入文字檔](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
