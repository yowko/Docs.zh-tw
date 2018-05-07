---
title: 如何：驗證 DBML 和外部對應檔
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 9bf21353aebd0ae57c51b2ddf3b31b5e7f1ac615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>如何：驗證 DBML 和外部對應檔
如果修改外部對應檔案和 .dbml 檔案，則必須根據它們各自的結構描述定義進行驗證。 本主題提供的步驟來實作驗證流程的 Visual Studio 使用者。  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a>若要驗證 .dbml 或 XML 檔案  
  
1.  在 Visual Studio**檔案**功能表上，指向**開啟**，然後按一下 **檔案**。  
  
2.  在**開啟檔案**對話方塊方塊中，按一下.dbml 或您想要驗證的 XML 對應檔案。  
  
     該檔案中開啟**XML 編輯器**。  
  
3.  視窗中，以滑鼠右鍵按一下，然後按一下 **屬性**。  
  
4.  在**屬性**視窗中，按一下省略符號**結構描述**屬性。  
  
     **XML 結構描述**對話方塊隨即開啟。  
  
5.  請記下適用於您目的的適當結構描述定義。  
  
    -   DbmlSchema.xsd 是用來驗證 .dbml 檔案的結構描述定義。 如需詳細資訊，請參閱[LINQ to SQL 中的程式碼產生](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)。  
  
    -   LinqToSqlMapping.xsd 是用來驗證外部 XML 對應檔案的結構描述定義。 如需詳細資訊，請參閱[外部對應](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)。  
  
6.  在**使用**所要結構描述定義資料列，按一下以開啟下拉式清單方塊中，然後按一下 資料行**使用此結構描述**。  
  
     結構描述定義檔案現在已經與 DBML 或 XML 對應檔案產生關聯。  
  
     請確定未選取其他結構描述定義。  
  
7.  在**檢視**功能表上，按一下 **錯誤清單**。  
  
     判斷是否已產生錯誤、警告或訊息。 如果未產生，則會根據結構描述定義驗證 XML 檔案為有效。  
  
## <a name="alternate-method-for-supplying-schema-definition"></a>提供結構描述定義的替代方法  
 如果基於某些原因適用的.xsd 檔案未出現在**XML 結構描述**對話方塊中，您可以從 [說明] 主題中下載.xsd 檔案。 下列步驟可協助您將下載的檔案儲存在所需的 Visual Studio XML 編輯器中的 Unicode 格式。  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>若要從說明主題中複製結構描述定義檔案  
  
1.  如這個主題前面所述，找到內含結構描述定義的 [說明] 主題。  
  
    -   .Dbml 檔案，請參閱[LINQ to SQL 中的程式碼產生](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)。  
  
    -   對於外部對應檔案，請參閱[外部對應](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)。  
  
2.  按一下**複製程式碼**將程式碼檔案複製到剪貼簿。  
  
3.  啟動 [記事本]，建立新的檔案。  
  
4.  將剪貼簿中的程式碼貼入 [記事本] 檔案中。  
  
5.  在 記事本**檔案**功能表上，按一下 **存**。  
  
6.  在**編碼**方塊中，選取**Unicode**。  
  
    > [!IMPORTANT]
    >  這個選項可確保會在文字檔前面加上 Unicode 16 位元組順序標記 (`FFFE`)。  
  
7.  在**檔案名稱**方塊中，建立副檔名為.xsd 的檔案名稱。  
  
## <a name="see-also"></a>另請參閱  
 [參考資料](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
