---
title: 安全及公開唯讀陣列欄位
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0110bb42775d8a5df9ca268b35db3abaffec84f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392625"
---
# <a name="security-and-public-read-only-array-fields"></a>安全及公開唯讀陣列欄位
永遠不會使用來自 managed 程式庫公用唯讀陣列欄位來定義的邊界行為或應用程式的安全性，因為可以修改公用唯讀陣列欄位。  
  
## <a name="remarks"></a>備註  
 某些.NET framework 類別包括唯讀包含平台特定界限參數的公用欄位。  例如，<xref:System.IO.Path.InvalidPathChars>欄位是陣列，其中描述檔案的路徑字串中不允許的字元。  許多類似的欄位會出現在.NET Framework。  
  
 公用唯讀欄位的值要<xref:System.IO.Path.InvalidPathChars>可以修改程式碼或共用您的程式碼應用程式定義域的程式碼。  您不應該使用像這樣的公用唯讀陣列欄位來定義應用程式界限的行為。  如果您這樣做，可以變更邊界定義惡意程式碼，並使用您程式碼中非預期的方式。  
  
 在版本 2.0 和更新版本的.NET Framework 中，您應該使用方法的傳回新的陣列，而不是使用公用陣列欄位。  例如，而不是使用<xref:System.IO.Path.InvalidPathChars> 欄位中，您應該使用<xref:System.IO.Path.GetInvalidPathChars%2A>方法。  
  
 請注意，.NET Framework 型別不會在內部定義界限類型使用公用欄位。  相反地，.NET Framework 會使用不同的私用欄位。  變更這些公用欄位的值不會改變行為的.NET Framework 型別。  
  
## <a name="see-also"></a>另請參閱  
 [安全程式碼撰寫方針](../../../docs/standard/security/secure-coding-guidelines.md)
