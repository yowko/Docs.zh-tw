---
title: 剪貼簿的格式無效
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7adc417d962de35272319d7dc976b237c7e2b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
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
