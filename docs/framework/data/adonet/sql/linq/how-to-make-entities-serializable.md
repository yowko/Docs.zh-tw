---
title: HOW TO：讓實體可序列化
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 5e9d078ed2daacfa48b09693f533e9aade613281
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002706"
---
# <a name="how-to-make-entities-serializable"></a>HOW TO：讓實體可序列化
在產生程式碼時，您可以讓實體成為可序列化。 實體類別會使用 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性予以裝飾，而資料行則使用 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性予以裝飾。  
  
 使用 Visual Studio 的開發人員可以使用物件關聯式設計工具來實現此目的。  
  
 如果您使用 SQLMetal 命令列工具，請使用 **/serialization**選項搭配 `unidirectional` 引數。 如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../tools/sqlmetal-exe-code-generation-tool.md)。  
  
## <a name="example"></a>範例  
 下列 SQLMetal 命令列會產生具有可序列化實體的檔案。  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a>另請參閱

- [序列化](serialization.md)
- [建立物件模型](creating-the-object-model.md)
