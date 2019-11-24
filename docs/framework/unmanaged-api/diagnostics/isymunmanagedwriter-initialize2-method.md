---
title: ISymUnmanagedWriter::Initialize2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
ms.openlocfilehash: 041df959139a0be77f40d6aa5655ff15f93fb26f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427953"
---
# <a name="isymunmanagedwriterinitialize2-method"></a>ISymUnmanagedWriter::Initialize2 方法
Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written. This method also lets you set the final location of the program database (PDB) file.  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a>參數  
 `emitter`  
 [in] A pointer to the metadata emitter interface.  
  
 `tempfilename`  
 [in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written. 如果檔案名稱是指定給不使用檔案名稱的寫入器，則這個參數會被忽略。  
  
 `pIStream`  
 [in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter. `pIStream` 是選擇性參數。  
  
 `fFullBuild`  
 [in] `true` if this is a full rebuild; `false` if this is an incremental compilation.  
  
 `finalfilename`  
 [in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.  
  
## <a name="return-value"></a>傳回值  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>需求  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>請參閱

- [ISymUnmanagedWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [Initialize 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)
