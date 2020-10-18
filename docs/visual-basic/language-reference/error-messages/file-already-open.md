---
title: 檔案已經開啟
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: ce8f8bf96d7355e45b2df82e8a131472c2ed2367
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162748"
---
# <a name="file-already-open"></a>檔案已經開啟

有時候必須先關閉檔案，才能 `FileOpen` 進行其他或其他操作。 可能導致本錯誤的原因包括：

- 已針對已開啟的檔案執行連續輸出模式作業 `FileOpen`

- 語句指的是開啟的檔案。

## <a name="to-correct-this-error"></a>更正這個錯誤

- 請先關閉檔案，再執行語句。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
