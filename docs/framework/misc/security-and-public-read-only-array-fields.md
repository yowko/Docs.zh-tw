---
title: 安全及公開唯讀陣列欄位
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19b5ad73150697c1442056642a1b11d504ecc426
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113772"
---
# <a name="security-and-public-read-only-array-fields"></a>安全及公開唯讀陣列欄位
定義界限的行為或應用程式的安全性，因為可以修改公用唯讀陣列欄位，從 managed 程式庫永遠不會使用公用唯讀陣列欄位。  
  
## <a name="remarks"></a>備註  
 某些.NET framework 類別包含唯讀的公用欄位，其中包含平台特定界限參數。  比方說，<xref:System.IO.Path.InvalidPathChars>欄位是陣列，描述檔案的路徑字串中不允許的字元。  許多類似的欄位會出現在.NET Framework 中。  
  
 公用的唯讀欄位的值要<xref:System.IO.Path.InvalidPathChars>可以修改您的程式碼或共用您的程式碼應用程式定義域的程式碼。  您不應該使用這類的公用唯讀陣列欄位來定義應用程式界限的行為。  如果您這樣做，惡意程式碼可以改變界限定義和非預期的方式使用您的程式碼。  
  
 在 2.0 版及更新版本的.NET Framework，您應該使用方法會傳回新的陣列，而不是使用公用陣列欄位。  比方說，而不是使用<xref:System.IO.Path.InvalidPathChars>欄位中，您應該使用<xref:System.IO.Path.GetInvalidPathChars%2A>方法。  
  
 請注意.NET Framework 型別不會在內部定義界限類型使用的公用欄位。  相反地，.NET Framework 會使用個別的私用欄位。  變更這些公用欄位的值不會改變行為的.NET Framework 型別。  
  
## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](../../../docs/standard/security/secure-coding-guidelines.md)
