---
title: ISymUnmanagedDocument 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
ms.openlocfilehash: 83c683e1f60f13f7cee4ddc6fe5af5a94e36eb93
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95692172"
---
# <a name="isymunmanageddocument-interface"></a>ISymUnmanagedDocument 介面

代表符號存放區所參考的文件。 檔是由統一資源定位器所定義 (URL) 和檔案類型 GUID。 您可以使用 [URL] 和 [檔案類型] GUID 來尋找檔，不論其儲存方式為何。 您可以將檔來源儲存在符號存放區中，並透過這個介面加以取出。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[FindClosestLine 方法](isymunmanageddocument-findclosestline-method.md)|如果本檔中不一定是序列點的行，則傳回最接近序列點的行。|  
|[GetCheckSum 方法](isymunmanageddocument-getchecksum-method.md)|取得總和檢查碼。|  
|[GetCheckSumAlgorithmId 方法](isymunmanageddocument-getchecksumalgorithmid-method.md)|取得總和檢查碼演算法識別碼，如果沒有總和檢查碼，則會傳回所有零的 GUID。|  
|[GetDocumentType 方法](isymunmanageddocument-getdocumenttype-method.md)|取得此檔的檔案類型。|  
|[GetLanguage 方法](isymunmanageddocument-getlanguage-method.md)|取得此檔的語言識別項。|  
|[GetLanguageVendor 方法](isymunmanageddocument-getlanguagevendor-method.md)|取得此檔的語言廠商。|  
|[GetSourceLength 方法](isymunmanageddocument-getsourcelength-method.md)|取得內嵌來源的長度 (以位元組為單位)。|  
|[GetSourceRange 方法](isymunmanageddocument-getsourcerange-method.md)|將內嵌來源的指定範圍傳回至指定的緩衝區。|  
|[GetURL 方法](isymunmanageddocument-geturl-method.md)|傳回此檔的 URL。|  
|[HasEmbeddedSource 方法](isymunmanageddocument-hasembeddedsource-method.md)|`true`如果檔具有內嵌在偵錯工具符號中的來源，則傳回，否則傳回 `false` 。|  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
