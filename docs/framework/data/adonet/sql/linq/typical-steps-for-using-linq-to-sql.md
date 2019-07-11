---
title: LINQ to SQL 的典型使用步驟
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: cbcd8099fd085d0198e5ba77ee0a3e86c1ca70d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742785"
---
# <a name="typical-steps-for-using-linq-to-sql"></a>LINQ to SQL 的典型使用步驟
若要實作 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式，請遵循本主題稍後所說明的步驟。 請注意，許多步驟都是選擇性的步驟。 您可以放心使用預設狀態下的物件模型。  
  
 快速入門中，使用物件關聯式設計工具來建立物件模型並且開始撰寫程式碼查詢。  
  
## <a name="creating-the-object-model"></a>建立物件模型  
 第一步是從現有關聯式資料庫的中繼資料 (Metadata) 建立物件模型。 物件模型會根據開發人員的程式設計語言來表示資料庫。 如需詳細資訊，請參閱 < [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)。  
  
### <a name="1-select-a-tool-to-create-the-model"></a>1.選取用以建立模型的工具。  
 用於建立模型的工具有三種。  
  
- 物件關聯式設計工具  
  
     這個設計工具提供了豐富的使用者介面，可用於從現有資料庫建立物件模型。 此工具是 Visual Studio IDE 的一部分，並最適合用於小型或中型資料庫。  
  
- SQLMetal 程式碼產生工具  
  
     此命令列公用程式會提供從 O/R 設計工具稍有不同組的選項。 若要建立大型資料庫的模型，使用這項工具最適合。 如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。  
  
- 程式碼編輯器  
  
     您可以使用 Visual Studio 程式碼編輯器或其他編輯器撰寫自己的程式碼。 不建議使用這種方法，您有現有的資料庫，並且可以使用 O/R 設計工具或 SQLMetal 工具時很容易發生錯誤。 但是，程式碼編輯器很適合用於調整您已經使用其他工具所產生的程式碼。 如需詳細資訊，請參閱[如何：使用程式碼編輯器自訂實體類別](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)。  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a>2.選取您要產生的程式碼種類。  
  
- C#或 Visual Basic 原始程式碼檔的屬性為基礎的對應。  
  
     然後，您會包含這個程式碼檔在 Visual Studio 專案中。 如需詳細資訊，請參閱 <<c0> [ 屬性為基礎的對應](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)。  
  
- XML 檔：適用於外部對應。  
  
     使用這種方法，您可以將對應中繼資料留在應用程式程式碼外。 如需詳細資訊，請參閱 <<c0> [ 外部對應](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)。  
  
    > [!NOTE]
    >  O/R 設計工具不支援產生外部對應檔。 您必須使用 SQLMetal 工具來實作這項功能。  
  
- DBML 檔：您可以在產生最終程式碼檔之前修改這個檔案。  
  
     這是一項進階功能。  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a>3.修改程式碼檔，以反映您的應用程式需求。  
 基於此目的，您可以使用 O/R 設計工具或程式碼編輯器。  
  
## <a name="using-the-object-model"></a>使用物件模型  
 下圖顯示在兩層式案例中，開發人員和資料之間的關係。 如需其他案例中，請參閱[多層式架構和遠端的應用程式使用 LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)。  
  
 ![如果螢幕擷取畫面顯示 Linq 物件模型。](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 您現在有了物件模型，接著就可以描述資訊要求以及操作該模型內的資料。 您會由物件模型中的物件和屬性觀點思考，而不是由資料庫的資料列和資料行觀點思考。 您不會直接處理資料庫。  
  
 當您指示[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]至執行您已描述的查詢或呼叫`SubmitChanges()`的資料，您已操作，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]與資料庫的語言中的資料庫進行通訊。  
  
 下列表示使用所建立之物件模型的一般步驟。  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a>1.建立查詢，以從資料庫擷取資訊。  
 如需詳細資訊，請參閱 <<c0> [ 查詢概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)並[查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)。  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a>2.覆寫 Insert、Update 和 Delete 的預設行為。  
 此步驟是具選擇性的。 如需詳細資訊，請參閱 <<c0> [ 自訂插入、 更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a>3.設定適當選項，以偵測和報告並行衝突。  
 您可以讓模型保有處理並行衝突時所用的預設值，也可加以變更以符合您的目的。 如需詳細資訊，請參閱[如何：指定的成員會用於測試並行衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)和[How to:指定時的並行存取例外狀況的擲回](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)。  
  
### <a name="4-establish-an-inheritance-hierarchy"></a>4.建立繼承階層架構。  
 此步驟是具選擇性的。 如需詳細資訊，請參閱 <<c0> [ 繼承支援](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)。  
  
### <a name="5-provide-an-appropriate-user-interface"></a>5.提供適當的使用者介面。  
 這個步驟是選擇性的步驟，要視應用程式的使用方式而定。  
  
### <a name="6-debug-and-test-your-application"></a>6.偵錯和測試應用程式。  
 如需詳細資訊，請參閱 <<c0> [ 偵錯支援](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)。  
  
## <a name="see-also"></a>另請參閱

- [快速入門](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
- [建立物件模型](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [預存程序](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
