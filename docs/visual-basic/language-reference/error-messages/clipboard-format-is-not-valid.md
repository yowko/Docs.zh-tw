---
title: 剪貼簿的格式無效
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 0a5d06b381df3af8de1d092b600239c9acfce39a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735775"
---
# <a name="clipboard-format-is-not-valid"></a>剪貼簿的格式無效
指定的剪貼簿格式與不相容所執行的方法。 此錯誤的可能原因包括：  
  
-   使用剪貼簿`GetText`或是`SetText`方法以外的剪貼簿格式`vbCFText`或`vbCFLink`。  
  
-   使用剪貼簿`GetData`或是`SetData`方法以外的剪貼簿格式`vbCFBitmap`， `vbCFDIB`，或`vbCFMetafile`。  
  
-   使用`GetData`或是`SetData`方法`DataObject`與 Microsoft Windows 登錄格式 （HC000-& HFFFF），保留範圍的剪貼簿格式時該剪貼簿格式尚未註冊使用 Microsoft Windows.  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移除無效的格式，並指定一個有效的帳戶。  
  
## <a name="see-also"></a>另請參閱
- [剪貼簿：加入其他格式](/cpp/mfc/clipboard-adding-other-formats)
