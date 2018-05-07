---
title: 剪貼簿的格式無效
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: eef16096b269902dbaca6a344abf4c5f6a504fb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="clipboard-format-is-not-valid"></a>剪貼簿的格式無效
指定的剪貼簿格式與不相容所執行的方法。 此錯誤的可能原因包括：  
  
-   使用剪貼簿`GetText`或`SetText`方法以外的剪貼簿格式`vbCFText`或`vbCFLink`。  
  
-   使用剪貼簿`GetData`或`SetData`方法以外的剪貼簿格式`vbCFBitmap`， `vbCFDIB`，或`vbCFMetafile`。  
  
-   使用`DataObject``GetData`方法或`SetData`與 Microsoft Windows 登錄格式 (HC000-& HFFFF)，保留範圍中的剪貼簿格式的方法時該剪貼簿格式尚未註冊使用 Microsoft Windows。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移除無效的格式，並指定為有效。  
  
## <a name="see-also"></a>另請參閱  
 [剪貼簿：新增其他格式](/cpp/mfc/clipboard-adding-other-formats)
