---
title: 不正確的檔案模式
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 534ea2d8316dc29cace798c5ad9b7697a290026f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409865"
---
# <a name="bad-file-mode"></a>不正確的檔案模式
用於操作檔案內容的語句，必須適合用來開啟檔案的模式。 可能的原因包括：  
  
- `FilePutObject`或 `FileGetObject` 語句指定了連續的檔案。  
  
- `Print`語句會指定針對或以外的存取模式開啟的檔案 `Output` `Append` 。  
  
- `Input`語句指定針對存取模式開啟的檔案，而非`Input`  
  
- 嘗試寫入唯讀檔案。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請確定 `FilePutObject` 和 `FileGetObject` 只會參考開啟 `Random` 或存取的檔案 `Binary` 。  
  
- 請確定 `Print` 指定針對 `Output` 或存取模式開啟的檔案 `Append` 。 如果不是，請使用不同的語句將資料放在檔案中，或在適當的模式中重新開啟檔案。  
  
- 請確定 `Input` 指定為開啟的檔案 `Input` 。 如果不是，請使用不同的語句將資料放在檔案中，或在適當的模式中重新開啟檔案。  
  
- 如果您要寫入唯讀檔案，請變更檔案的讀取/寫入狀態，或不要嘗試寫入檔案。  
  
- 使用 `My.Computer.FileSystem` 物件中可用的功能。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileSystem>
- [疑難排解：讀取和寫入文字檔](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
