---
title: ODBC 結構描述集合
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: 072a9cd365031cd5660d1824bc229d459abc5af8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525829"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="7767d-102">ODBC 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="7767d-102">ODBC Schema Collections</span></span>
<span data-ttu-id="7767d-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 ODBC 驅動程式的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="7767d-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="7767d-104">Microsoft SQL Server ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="7767d-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="7767d-105">Microsoft SQL Server ODBC 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="7767d-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="7767d-106">資料表</span><span class="sxs-lookup"><span data-stu-id="7767d-106">Tables</span></span>  
  
-   <span data-ttu-id="7767d-107">Indexes</span><span class="sxs-lookup"><span data-stu-id="7767d-107">Indexes</span></span>  
  
-   <span data-ttu-id="7767d-108">資料行</span><span class="sxs-lookup"><span data-stu-id="7767d-108">Columns</span></span>  
  
-   <span data-ttu-id="7767d-109">程序</span><span class="sxs-lookup"><span data-stu-id="7767d-109">Procedures</span></span>  
  
-   <span data-ttu-id="7767d-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="7767d-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="7767d-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="7767d-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="7767d-112">檢視</span><span class="sxs-lookup"><span data-stu-id="7767d-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="7767d-113">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="7767d-113">Tables and Views</span></span>  
  
|<span data-ttu-id="7767d-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="7767d-114">ColumnName</span></span>|<span data-ttu-id="7767d-115">DataType</span><span class="sxs-lookup"><span data-stu-id="7767d-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7767d-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="7767d-116">TABLE_CAT</span></span>|<span data-ttu-id="7767d-117">String</span><span class="sxs-lookup"><span data-stu-id="7767d-117">String</span></span>|  
|<span data-ttu-id="7767d-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="7767d-118">TABLE_SCHEM</span></span>|<span data-ttu-id="7767d-119">String</span><span class="sxs-lookup"><span data-stu-id="7767d-119">String</span></span>|  
|<span data-ttu-id="7767d-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-120">TABLE_NAME</span></span>|<span data-ttu-id="7767d-121">String</span><span class="sxs-lookup"><span data-stu-id="7767d-121">String</span></span>|  
|<span data-ttu-id="7767d-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-122">TABLE_TYPE</span></span>|<span data-ttu-id="7767d-123">String</span><span class="sxs-lookup"><span data-stu-id="7767d-123">String</span></span>|  
|<span data-ttu-id="7767d-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="7767d-124">REMARKS</span></span>|<span data-ttu-id="7767d-125">String</span><span class="sxs-lookup"><span data-stu-id="7767d-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="7767d-126">Indexes</span><span class="sxs-lookup"><span data-stu-id="7767d-126">Indexes</span></span>  
  
|<span data-ttu-id="7767d-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="7767d-127">ColumnName</span></span>|<span data-ttu-id="7767d-128">DataType</span><span class="sxs-lookup"><span data-stu-id="7767d-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7767d-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="7767d-129">TABLE_CAT</span></span>|<span data-ttu-id="7767d-130">String</span><span class="sxs-lookup"><span data-stu-id="7767d-130">String</span></span>|  
|<span data-ttu-id="7767d-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="7767d-131">TABLE_SCHEM</span></span>|<span data-ttu-id="7767d-132">String</span><span class="sxs-lookup"><span data-stu-id="7767d-132">String</span></span>|  
|<span data-ttu-id="7767d-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-133">TABLE_NAME</span></span>|<span data-ttu-id="7767d-134">String</span><span class="sxs-lookup"><span data-stu-id="7767d-134">String</span></span>|  
|<span data-ttu-id="7767d-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="7767d-135">NON_UNIQUE</span></span>|<span data-ttu-id="7767d-136">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-136">Int16</span></span>|  
|<span data-ttu-id="7767d-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7767d-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="7767d-138">String</span><span class="sxs-lookup"><span data-stu-id="7767d-138">String</span></span>|  
|<span data-ttu-id="7767d-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-139">INDEX_NAME</span></span>|<span data-ttu-id="7767d-140">String</span><span class="sxs-lookup"><span data-stu-id="7767d-140">String</span></span>|  
|<span data-ttu-id="7767d-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-141">TYPE</span></span>|<span data-ttu-id="7767d-142">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-142">Int16</span></span>|  
|<span data-ttu-id="7767d-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7767d-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="7767d-144">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-144">Int16</span></span>|  
|<span data-ttu-id="7767d-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-145">COLUMN_NAME</span></span>|<span data-ttu-id="7767d-146">String</span><span class="sxs-lookup"><span data-stu-id="7767d-146">String</span></span>|  
|<span data-ttu-id="7767d-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="7767d-147">ASC_OR_DESC</span></span>|<span data-ttu-id="7767d-148">String</span><span class="sxs-lookup"><span data-stu-id="7767d-148">String</span></span>|  
|<span data-ttu-id="7767d-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="7767d-149">CARDINATLITY</span></span>|<span data-ttu-id="7767d-150">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-150">Int32</span></span>|  
|<span data-ttu-id="7767d-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="7767d-151">PAGES</span></span>|<span data-ttu-id="7767d-152">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-152">Int32</span></span>|  
|<span data-ttu-id="7767d-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="7767d-153">FILTER_CONDITION</span></span>|<span data-ttu-id="7767d-154">String</span><span class="sxs-lookup"><span data-stu-id="7767d-154">String</span></span>|  
|<span data-ttu-id="7767d-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7767d-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="7767d-156">String</span><span class="sxs-lookup"><span data-stu-id="7767d-156">String</span></span>|  
|<span data-ttu-id="7767d-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="7767d-158">Byte</span><span class="sxs-lookup"><span data-stu-id="7767d-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="7767d-159">資料行</span><span class="sxs-lookup"><span data-stu-id="7767d-159">Columns</span></span>  
  
|<span data-ttu-id="7767d-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="7767d-160">ColumnName</span></span>|<span data-ttu-id="7767d-161">DataType</span><span class="sxs-lookup"><span data-stu-id="7767d-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7767d-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="7767d-162">TABLE_CAT</span></span>|<span data-ttu-id="7767d-163">String</span><span class="sxs-lookup"><span data-stu-id="7767d-163">String</span></span>|  
|<span data-ttu-id="7767d-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="7767d-164">TABLE_SCHEM</span></span>|<span data-ttu-id="7767d-165">String</span><span class="sxs-lookup"><span data-stu-id="7767d-165">String</span></span>|  
|<span data-ttu-id="7767d-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-166">TABLE_NAME</span></span>|<span data-ttu-id="7767d-167">String</span><span class="sxs-lookup"><span data-stu-id="7767d-167">String</span></span>|  
|<span data-ttu-id="7767d-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-168">COLUMN_NAME</span></span>|<span data-ttu-id="7767d-169">String</span><span class="sxs-lookup"><span data-stu-id="7767d-169">String</span></span>|  
|<span data-ttu-id="7767d-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-170">DATA_TYPE</span></span>|<span data-ttu-id="7767d-171">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-171">Int16</span></span>|  
|<span data-ttu-id="7767d-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-172">TYPE_NAME</span></span>|<span data-ttu-id="7767d-173">String</span><span class="sxs-lookup"><span data-stu-id="7767d-173">String</span></span>|  
|<span data-ttu-id="7767d-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="7767d-174">COLUMN_SIZE</span></span>|<span data-ttu-id="7767d-175">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-175">Int32</span></span>|  
|<span data-ttu-id="7767d-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="7767d-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="7767d-177">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-177">Int32</span></span>|  
|<span data-ttu-id="7767d-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="7767d-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="7767d-179">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-179">Int16</span></span>|  
|<span data-ttu-id="7767d-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="7767d-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="7767d-181">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-181">Int16</span></span>|  
|<span data-ttu-id="7767d-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="7767d-182">NULLABLE</span></span>|<span data-ttu-id="7767d-183">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-183">Int16</span></span>|  
|<span data-ttu-id="7767d-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="7767d-184">REMARKS</span></span>|<span data-ttu-id="7767d-185">String</span><span class="sxs-lookup"><span data-stu-id="7767d-185">String</span></span>|  
|<span data-ttu-id="7767d-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="7767d-186">COLUMN_DEF</span></span>|<span data-ttu-id="7767d-187">String</span><span class="sxs-lookup"><span data-stu-id="7767d-187">String</span></span>|  
|<span data-ttu-id="7767d-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="7767d-189">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-189">Int16</span></span>|  
|<span data-ttu-id="7767d-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="7767d-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="7767d-191">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-191">Int16</span></span>|  
|<span data-ttu-id="7767d-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="7767d-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="7767d-193">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-193">Int32</span></span>|  
|<span data-ttu-id="7767d-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7767d-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="7767d-195">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-195">Int32</span></span>|  
|<span data-ttu-id="7767d-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="7767d-196">IS_NULLABLE</span></span>|<span data-ttu-id="7767d-197">String</span><span class="sxs-lookup"><span data-stu-id="7767d-197">String</span></span>|  
|<span data-ttu-id="7767d-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7767d-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="7767d-199">String</span><span class="sxs-lookup"><span data-stu-id="7767d-199">String</span></span>|  
|<span data-ttu-id="7767d-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7767d-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="7767d-201">String</span><span class="sxs-lookup"><span data-stu-id="7767d-201">String</span></span>|  
|<span data-ttu-id="7767d-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="7767d-203">Byte</span><span class="sxs-lookup"><span data-stu-id="7767d-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="7767d-204">程序</span><span class="sxs-lookup"><span data-stu-id="7767d-204">Procedures</span></span>  
  
|<span data-ttu-id="7767d-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="7767d-205">ColumnName</span></span>|<span data-ttu-id="7767d-206">DataType</span><span class="sxs-lookup"><span data-stu-id="7767d-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7767d-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="7767d-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="7767d-208">String</span><span class="sxs-lookup"><span data-stu-id="7767d-208">String</span></span>|  
|<span data-ttu-id="7767d-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="7767d-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="7767d-210">String</span><span class="sxs-lookup"><span data-stu-id="7767d-210">String</span></span>|  
|<span data-ttu-id="7767d-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="7767d-212">String</span><span class="sxs-lookup"><span data-stu-id="7767d-212">String</span></span>|  
|<span data-ttu-id="7767d-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="7767d-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="7767d-214">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-214">Int32</span></span>|  
|<span data-ttu-id="7767d-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="7767d-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="7767d-216">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-216">Int32</span></span>|  
|<span data-ttu-id="7767d-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="7767d-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="7767d-218">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-218">Int32</span></span>|  
|<span data-ttu-id="7767d-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="7767d-219">REMARKS</span></span>|<span data-ttu-id="7767d-220">String</span><span class="sxs-lookup"><span data-stu-id="7767d-220">String</span></span>|  
|<span data-ttu-id="7767d-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="7767d-222">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="7767d-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="7767d-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="7767d-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="7767d-224">ColumnName</span></span>|<span data-ttu-id="7767d-225">DataType</span><span class="sxs-lookup"><span data-stu-id="7767d-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7767d-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="7767d-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="7767d-227">String</span><span class="sxs-lookup"><span data-stu-id="7767d-227">String</span></span>|  
|<span data-ttu-id="7767d-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="7767d-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="7767d-229">String</span><span class="sxs-lookup"><span data-stu-id="7767d-229">String</span></span>|  
|<span data-ttu-id="7767d-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="7767d-231">String</span><span class="sxs-lookup"><span data-stu-id="7767d-231">String</span></span>|  
|<span data-ttu-id="7767d-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-232">COLUMN_NAME</span></span>|<span data-ttu-id="7767d-233">String</span><span class="sxs-lookup"><span data-stu-id="7767d-233">String</span></span>|  
|<span data-ttu-id="7767d-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-234">COLUMN_TYPE</span></span>|<span data-ttu-id="7767d-235">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-235">Int16</span></span>|  
|<span data-ttu-id="7767d-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-236">DATA_TYPE</span></span>|<span data-ttu-id="7767d-237">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-237">Int16</span></span>|  
|<span data-ttu-id="7767d-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-238">TYPE_NAME</span></span>|<span data-ttu-id="7767d-239">String</span><span class="sxs-lookup"><span data-stu-id="7767d-239">String</span></span>|  
|<span data-ttu-id="7767d-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="7767d-240">COLUMN_SIZE</span></span>|<span data-ttu-id="7767d-241">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-241">Int32</span></span>|  
|<span data-ttu-id="7767d-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="7767d-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="7767d-243">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-243">Int32</span></span>|  
|<span data-ttu-id="7767d-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="7767d-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="7767d-245">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-245">Int16</span></span>|  
|<span data-ttu-id="7767d-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="7767d-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="7767d-247">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-247">Int16</span></span>|  
|<span data-ttu-id="7767d-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="7767d-248">NULLABLE</span></span>|<span data-ttu-id="7767d-249">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-249">Int16</span></span>|  
|<span data-ttu-id="7767d-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="7767d-250">REMARKS</span></span>|<span data-ttu-id="7767d-251">String</span><span class="sxs-lookup"><span data-stu-id="7767d-251">String</span></span>|  
|<span data-ttu-id="7767d-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="7767d-252">COLUMN_DEF</span></span>|<span data-ttu-id="7767d-253">String</span><span class="sxs-lookup"><span data-stu-id="7767d-253">String</span></span>|  
|<span data-ttu-id="7767d-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="7767d-255">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-255">Int16</span></span>|  
|<span data-ttu-id="7767d-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="7767d-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="7767d-257">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-257">Int16</span></span>|  
|<span data-ttu-id="7767d-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="7767d-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="7767d-259">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-259">Int32</span></span>|  
|<span data-ttu-id="7767d-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7767d-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="7767d-261">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-261">Int32</span></span>|  
|<span data-ttu-id="7767d-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="7767d-262">IS_NULLABLE</span></span>|<span data-ttu-id="7767d-263">String</span><span class="sxs-lookup"><span data-stu-id="7767d-263">String</span></span>|  
|<span data-ttu-id="7767d-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7767d-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="7767d-265">String</span><span class="sxs-lookup"><span data-stu-id="7767d-265">String</span></span>|  
|<span data-ttu-id="7767d-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7767d-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="7767d-267">String</span><span class="sxs-lookup"><span data-stu-id="7767d-267">String</span></span>|  
|<span data-ttu-id="7767d-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="7767d-269">Byte</span><span class="sxs-lookup"><span data-stu-id="7767d-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="7767d-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="7767d-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="7767d-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="7767d-271">ColumnName</span></span>|<span data-ttu-id="7767d-272">DataType</span><span class="sxs-lookup"><span data-stu-id="7767d-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7767d-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="7767d-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="7767d-274">String</span><span class="sxs-lookup"><span data-stu-id="7767d-274">String</span></span>|  
|<span data-ttu-id="7767d-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="7767d-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="7767d-276">String</span><span class="sxs-lookup"><span data-stu-id="7767d-276">String</span></span>|  
|<span data-ttu-id="7767d-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="7767d-278">String</span><span class="sxs-lookup"><span data-stu-id="7767d-278">String</span></span>|  
|<span data-ttu-id="7767d-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-279">COLUMN_NAME</span></span>|<span data-ttu-id="7767d-280">String</span><span class="sxs-lookup"><span data-stu-id="7767d-280">String</span></span>|  
|<span data-ttu-id="7767d-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-281">COLUMN_TYPE</span></span>|<span data-ttu-id="7767d-282">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-282">Int16</span></span>|  
|<span data-ttu-id="7767d-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-283">DATA_TYPE</span></span>|<span data-ttu-id="7767d-284">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-284">Int16</span></span>|  
|<span data-ttu-id="7767d-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-285">TYPE_NAME</span></span>|<span data-ttu-id="7767d-286">String</span><span class="sxs-lookup"><span data-stu-id="7767d-286">String</span></span>|  
|<span data-ttu-id="7767d-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="7767d-287">COLUMN_SIZE</span></span>|<span data-ttu-id="7767d-288">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-288">Int32</span></span>|  
|<span data-ttu-id="7767d-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="7767d-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="7767d-290">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-290">Int32</span></span>|  
|<span data-ttu-id="7767d-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="7767d-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="7767d-292">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-292">Int16</span></span>|  
|<span data-ttu-id="7767d-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="7767d-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="7767d-294">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-294">Int16</span></span>|  
|<span data-ttu-id="7767d-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="7767d-295">NULLABLE</span></span>|<span data-ttu-id="7767d-296">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-296">Int16</span></span>|  
|<span data-ttu-id="7767d-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="7767d-297">REMARKS</span></span>|<span data-ttu-id="7767d-298">String</span><span class="sxs-lookup"><span data-stu-id="7767d-298">String</span></span>|  
|<span data-ttu-id="7767d-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="7767d-299">COLUMN_DEF</span></span>|<span data-ttu-id="7767d-300">String</span><span class="sxs-lookup"><span data-stu-id="7767d-300">String</span></span>|  
|<span data-ttu-id="7767d-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="7767d-302">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-302">Int16</span></span>|  
|<span data-ttu-id="7767d-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="7767d-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="7767d-304">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-304">Int16</span></span>|  
|<span data-ttu-id="7767d-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="7767d-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="7767d-306">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-306">Int32</span></span>|  
|<span data-ttu-id="7767d-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7767d-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="7767d-308">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-308">Int32</span></span>|  
|<span data-ttu-id="7767d-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="7767d-309">IS_NULLABLE</span></span>|<span data-ttu-id="7767d-310">String</span><span class="sxs-lookup"><span data-stu-id="7767d-310">String</span></span>|  
|<span data-ttu-id="7767d-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7767d-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="7767d-312">String</span><span class="sxs-lookup"><span data-stu-id="7767d-312">String</span></span>|  
|<span data-ttu-id="7767d-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7767d-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="7767d-314">String</span><span class="sxs-lookup"><span data-stu-id="7767d-314">String</span></span>|  
|<span data-ttu-id="7767d-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="7767d-316">Byte</span><span class="sxs-lookup"><span data-stu-id="7767d-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="7767d-317">Microsoft Oracle ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="7767d-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="7767d-318">Microsoft SQL Server Oracle ODBC 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="7767d-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="7767d-319">資料表</span><span class="sxs-lookup"><span data-stu-id="7767d-319">Tables</span></span>  
  
-   <span data-ttu-id="7767d-320">資料行</span><span class="sxs-lookup"><span data-stu-id="7767d-320">Columns</span></span>  
  
-   <span data-ttu-id="7767d-321">程序</span><span class="sxs-lookup"><span data-stu-id="7767d-321">Procedures</span></span>  
  
-   <span data-ttu-id="7767d-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="7767d-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="7767d-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="7767d-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="7767d-324">檢視</span><span class="sxs-lookup"><span data-stu-id="7767d-324">Views</span></span>  
  
-   <span data-ttu-id="7767d-325">Indexes</span><span class="sxs-lookup"><span data-stu-id="7767d-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="7767d-326">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="7767d-326">Tables and Views</span></span>  
  
|<span data-ttu-id="7767d-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="7767d-327">ColumnName</span></span>|<span data-ttu-id="7767d-328">DataType</span><span class="sxs-lookup"><span data-stu-id="7767d-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7767d-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7767d-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="7767d-330">String</span><span class="sxs-lookup"><span data-stu-id="7767d-330">String</span></span>|  
|<span data-ttu-id="7767d-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="7767d-331">TABLE_OWNER</span></span>|<span data-ttu-id="7767d-332">String</span><span class="sxs-lookup"><span data-stu-id="7767d-332">String</span></span>|  
|<span data-ttu-id="7767d-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-333">TABLE_NAME</span></span>|<span data-ttu-id="7767d-334">String</span><span class="sxs-lookup"><span data-stu-id="7767d-334">String</span></span>|  
|<span data-ttu-id="7767d-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-335">TABLE_TYPE</span></span>|<span data-ttu-id="7767d-336">String</span><span class="sxs-lookup"><span data-stu-id="7767d-336">String</span></span>|  
|<span data-ttu-id="7767d-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="7767d-337">REMARKS</span></span>|<span data-ttu-id="7767d-338">String</span><span class="sxs-lookup"><span data-stu-id="7767d-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="7767d-339">資料行</span><span class="sxs-lookup"><span data-stu-id="7767d-339">Columns</span></span>  
  
|<span data-ttu-id="7767d-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="7767d-340">ColumnName</span></span>|<span data-ttu-id="7767d-341">DataType</span><span class="sxs-lookup"><span data-stu-id="7767d-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7767d-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7767d-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="7767d-343">String</span><span class="sxs-lookup"><span data-stu-id="7767d-343">String</span></span>|  
|<span data-ttu-id="7767d-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="7767d-344">TABLE_OWNER</span></span>|<span data-ttu-id="7767d-345">String</span><span class="sxs-lookup"><span data-stu-id="7767d-345">String</span></span>|  
|<span data-ttu-id="7767d-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-346">TABLE_NAME</span></span>|<span data-ttu-id="7767d-347">String</span><span class="sxs-lookup"><span data-stu-id="7767d-347">String</span></span>|  
|<span data-ttu-id="7767d-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-348">COLUMN_NAME</span></span>|<span data-ttu-id="7767d-349">String</span><span class="sxs-lookup"><span data-stu-id="7767d-349">String</span></span>|  
|<span data-ttu-id="7767d-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-350">DATA_TYPE</span></span>|<span data-ttu-id="7767d-351">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-351">Int16</span></span>|  
|<span data-ttu-id="7767d-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-352">TYPE_NAME</span></span>|<span data-ttu-id="7767d-353">String</span><span class="sxs-lookup"><span data-stu-id="7767d-353">String</span></span>|  
|<span data-ttu-id="7767d-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="7767d-354">PRECISION</span></span>|<span data-ttu-id="7767d-355">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-355">Int32</span></span>|  
|<span data-ttu-id="7767d-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="7767d-356">LENGTH</span></span>|<span data-ttu-id="7767d-357">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-357">Int32</span></span>|  
|<span data-ttu-id="7767d-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="7767d-358">SCALE</span></span>|<span data-ttu-id="7767d-359">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-359">Int16</span></span>|  
|<span data-ttu-id="7767d-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="7767d-360">RADIX</span></span>|<span data-ttu-id="7767d-361">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-361">Int16</span></span>|  
|<span data-ttu-id="7767d-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="7767d-362">NULLABLE</span></span>|<span data-ttu-id="7767d-363">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-363">Int16</span></span>|  
|<span data-ttu-id="7767d-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="7767d-364">REMARKS</span></span>|<span data-ttu-id="7767d-365">String</span><span class="sxs-lookup"><span data-stu-id="7767d-365">String</span></span>|  
|<span data-ttu-id="7767d-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7767d-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="7767d-367">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="7767d-368">程序</span><span class="sxs-lookup"><span data-stu-id="7767d-368">Procedures</span></span>  
  
|<span data-ttu-id="7767d-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="7767d-369">ColumnName</span></span>|<span data-ttu-id="7767d-370">DataType</span><span class="sxs-lookup"><span data-stu-id="7767d-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7767d-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7767d-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="7767d-372">String</span><span class="sxs-lookup"><span data-stu-id="7767d-372">String</span></span>|  
|<span data-ttu-id="7767d-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="7767d-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="7767d-374">String</span><span class="sxs-lookup"><span data-stu-id="7767d-374">String</span></span>|  
|<span data-ttu-id="7767d-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="7767d-376">String</span><span class="sxs-lookup"><span data-stu-id="7767d-376">String</span></span>|  
|<span data-ttu-id="7767d-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="7767d-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="7767d-378">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-378">Int16</span></span>|  
|<span data-ttu-id="7767d-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="7767d-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="7767d-380">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-380">Int16</span></span>|  
|<span data-ttu-id="7767d-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="7767d-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="7767d-382">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-382">Int16</span></span>|  
|<span data-ttu-id="7767d-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="7767d-383">REMARKS</span></span>|<span data-ttu-id="7767d-384">String</span><span class="sxs-lookup"><span data-stu-id="7767d-384">String</span></span>|  
|<span data-ttu-id="7767d-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="7767d-386">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="7767d-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="7767d-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="7767d-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="7767d-388">ColumnName</span></span>|<span data-ttu-id="7767d-389">DataType</span><span class="sxs-lookup"><span data-stu-id="7767d-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7767d-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7767d-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="7767d-391">String</span><span class="sxs-lookup"><span data-stu-id="7767d-391">String</span></span>|  
|<span data-ttu-id="7767d-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="7767d-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="7767d-393">String</span><span class="sxs-lookup"><span data-stu-id="7767d-393">String</span></span>|  
|<span data-ttu-id="7767d-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="7767d-395">String</span><span class="sxs-lookup"><span data-stu-id="7767d-395">String</span></span>|  
|<span data-ttu-id="7767d-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-396">COLUMN_NAME</span></span>|<span data-ttu-id="7767d-397">String</span><span class="sxs-lookup"><span data-stu-id="7767d-397">String</span></span>|  
|<span data-ttu-id="7767d-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-398">COLUMN_TYPE</span></span>|<span data-ttu-id="7767d-399">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-399">Int16</span></span>|  
|<span data-ttu-id="7767d-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-400">DATA_TYPE</span></span>|<span data-ttu-id="7767d-401">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-401">Int16</span></span>|  
|<span data-ttu-id="7767d-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-402">TYPE_NAME</span></span>|<span data-ttu-id="7767d-403">String</span><span class="sxs-lookup"><span data-stu-id="7767d-403">String</span></span>|  
|<span data-ttu-id="7767d-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="7767d-404">PRECISION</span></span>|<span data-ttu-id="7767d-405">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-405">Int32</span></span>|  
|<span data-ttu-id="7767d-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="7767d-406">LENGTH</span></span>|<span data-ttu-id="7767d-407">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-407">Int32</span></span>|  
|<span data-ttu-id="7767d-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="7767d-408">SCALE</span></span>|<span data-ttu-id="7767d-409">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-409">Int16</span></span>|  
|<span data-ttu-id="7767d-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="7767d-410">RADIX</span></span>|<span data-ttu-id="7767d-411">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-411">Int16</span></span>|  
|<span data-ttu-id="7767d-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="7767d-412">NULLABLE</span></span>|<span data-ttu-id="7767d-413">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-413">Int16</span></span>|  
|<span data-ttu-id="7767d-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="7767d-414">REMARKS</span></span>|<span data-ttu-id="7767d-415">String</span><span class="sxs-lookup"><span data-stu-id="7767d-415">String</span></span>|  
|<span data-ttu-id="7767d-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="7767d-416">OVERLOAD</span></span>|<span data-ttu-id="7767d-417">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-417">Int32</span></span>|  
|<span data-ttu-id="7767d-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7767d-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="7767d-419">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="7767d-420">Microsoft Jet ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="7767d-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="7767d-421">除了通用結構描述集合之外，Microsoft Jet ODBC 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="7767d-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="7767d-422">資料表</span><span class="sxs-lookup"><span data-stu-id="7767d-422">Tables</span></span>  
  
-   <span data-ttu-id="7767d-423">Indexes</span><span class="sxs-lookup"><span data-stu-id="7767d-423">Indexes</span></span>  
  
-   <span data-ttu-id="7767d-424">資料行</span><span class="sxs-lookup"><span data-stu-id="7767d-424">Columns</span></span>  
  
-   <span data-ttu-id="7767d-425">程序</span><span class="sxs-lookup"><span data-stu-id="7767d-425">Procedures</span></span>  
  
-   <span data-ttu-id="7767d-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="7767d-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="7767d-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="7767d-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="7767d-428">檢視</span><span class="sxs-lookup"><span data-stu-id="7767d-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="7767d-429">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="7767d-429">Tables and Views</span></span>  
  
|<span data-ttu-id="7767d-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="7767d-430">ColumnName</span></span>|<span data-ttu-id="7767d-431">DataType</span><span class="sxs-lookup"><span data-stu-id="7767d-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7767d-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7767d-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="7767d-433">String</span><span class="sxs-lookup"><span data-stu-id="7767d-433">String</span></span>|  
|<span data-ttu-id="7767d-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="7767d-434">TABLE_OWNER</span></span>|<span data-ttu-id="7767d-435">String</span><span class="sxs-lookup"><span data-stu-id="7767d-435">String</span></span>|  
|<span data-ttu-id="7767d-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-436">TABLE_NAME</span></span>|<span data-ttu-id="7767d-437">String</span><span class="sxs-lookup"><span data-stu-id="7767d-437">String</span></span>|  
|<span data-ttu-id="7767d-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-438">TABLE_TYPE</span></span>|<span data-ttu-id="7767d-439">String</span><span class="sxs-lookup"><span data-stu-id="7767d-439">String</span></span>|  
|<span data-ttu-id="7767d-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="7767d-440">REMARKS</span></span>|<span data-ttu-id="7767d-441">String</span><span class="sxs-lookup"><span data-stu-id="7767d-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="7767d-442">資料行</span><span class="sxs-lookup"><span data-stu-id="7767d-442">Columns</span></span>  
  
|<span data-ttu-id="7767d-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="7767d-443">ColumnName</span></span>|<span data-ttu-id="7767d-444">DataType</span><span class="sxs-lookup"><span data-stu-id="7767d-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7767d-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7767d-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="7767d-446">String</span><span class="sxs-lookup"><span data-stu-id="7767d-446">String</span></span>|  
|<span data-ttu-id="7767d-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="7767d-447">TABLE_OWNER</span></span>|<span data-ttu-id="7767d-448">String</span><span class="sxs-lookup"><span data-stu-id="7767d-448">String</span></span>|  
|<span data-ttu-id="7767d-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-449">TABLE_NAME</span></span>|<span data-ttu-id="7767d-450">String</span><span class="sxs-lookup"><span data-stu-id="7767d-450">String</span></span>|  
|<span data-ttu-id="7767d-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-451">COLUMN_NAME</span></span>|<span data-ttu-id="7767d-452">String</span><span class="sxs-lookup"><span data-stu-id="7767d-452">String</span></span>|  
|<span data-ttu-id="7767d-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-453">DATA_TYPE</span></span>|<span data-ttu-id="7767d-454">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-454">Int16</span></span>|  
|<span data-ttu-id="7767d-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-455">TYPE_NAME</span></span>|<span data-ttu-id="7767d-456">String</span><span class="sxs-lookup"><span data-stu-id="7767d-456">String</span></span>|  
|<span data-ttu-id="7767d-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="7767d-457">PRECISION</span></span>|<span data-ttu-id="7767d-458">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-458">Int32</span></span>|  
|<span data-ttu-id="7767d-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="7767d-459">LENGTH</span></span>|<span data-ttu-id="7767d-460">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-460">Int32</span></span>|  
|<span data-ttu-id="7767d-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="7767d-461">SCALE</span></span>|<span data-ttu-id="7767d-462">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-462">Int16</span></span>|  
|<span data-ttu-id="7767d-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="7767d-463">RADIX</span></span>|<span data-ttu-id="7767d-464">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-464">Int16</span></span>|  
|<span data-ttu-id="7767d-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="7767d-465">NULLABLE</span></span>|<span data-ttu-id="7767d-466">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-466">Int16</span></span>|  
|<span data-ttu-id="7767d-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="7767d-467">REMARKS</span></span>|<span data-ttu-id="7767d-468">String</span><span class="sxs-lookup"><span data-stu-id="7767d-468">String</span></span>|  
|<span data-ttu-id="7767d-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7767d-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="7767d-470">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="7767d-471">程序</span><span class="sxs-lookup"><span data-stu-id="7767d-471">Procedures</span></span>  
  
|<span data-ttu-id="7767d-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="7767d-472">ColumnName</span></span>|<span data-ttu-id="7767d-473">DataType</span><span class="sxs-lookup"><span data-stu-id="7767d-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7767d-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7767d-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="7767d-475">String</span><span class="sxs-lookup"><span data-stu-id="7767d-475">String</span></span>|  
|<span data-ttu-id="7767d-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="7767d-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="7767d-477">String</span><span class="sxs-lookup"><span data-stu-id="7767d-477">String</span></span>|  
|<span data-ttu-id="7767d-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="7767d-479">String</span><span class="sxs-lookup"><span data-stu-id="7767d-479">String</span></span>|  
|<span data-ttu-id="7767d-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="7767d-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="7767d-481">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-481">Int16</span></span>|  
|<span data-ttu-id="7767d-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="7767d-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="7767d-483">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-483">Int16</span></span>|  
|<span data-ttu-id="7767d-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="7767d-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="7767d-485">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-485">Int16</span></span>|  
|<span data-ttu-id="7767d-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="7767d-486">REMARKS</span></span>|<span data-ttu-id="7767d-487">String</span><span class="sxs-lookup"><span data-stu-id="7767d-487">String</span></span>|  
|<span data-ttu-id="7767d-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="7767d-489">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="7767d-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="7767d-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="7767d-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="7767d-491">ColumnName</span></span>|<span data-ttu-id="7767d-492">DataType</span><span class="sxs-lookup"><span data-stu-id="7767d-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7767d-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="7767d-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="7767d-494">String</span><span class="sxs-lookup"><span data-stu-id="7767d-494">String</span></span>|  
|<span data-ttu-id="7767d-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="7767d-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="7767d-496">String</span><span class="sxs-lookup"><span data-stu-id="7767d-496">String</span></span>|  
|<span data-ttu-id="7767d-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="7767d-498">String</span><span class="sxs-lookup"><span data-stu-id="7767d-498">String</span></span>|  
|<span data-ttu-id="7767d-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-499">COLUMN_NAME</span></span>|<span data-ttu-id="7767d-500">String</span><span class="sxs-lookup"><span data-stu-id="7767d-500">String</span></span>|  
|<span data-ttu-id="7767d-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-501">COLUMN_TYPE</span></span>|<span data-ttu-id="7767d-502">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-502">Int16</span></span>|  
|<span data-ttu-id="7767d-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-503">DATA_TYPE</span></span>|<span data-ttu-id="7767d-504">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-504">Int16</span></span>|  
|<span data-ttu-id="7767d-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-505">TYPE_NAME</span></span>|<span data-ttu-id="7767d-506">String</span><span class="sxs-lookup"><span data-stu-id="7767d-506">String</span></span>|  
|<span data-ttu-id="7767d-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="7767d-507">PRECISION</span></span>|<span data-ttu-id="7767d-508">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-508">Int32</span></span>|  
|<span data-ttu-id="7767d-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="7767d-509">LENGTH</span></span>|<span data-ttu-id="7767d-510">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-510">Int32</span></span>|  
|<span data-ttu-id="7767d-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="7767d-511">SCALE</span></span>|<span data-ttu-id="7767d-512">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-512">Int16</span></span>|  
|<span data-ttu-id="7767d-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="7767d-513">RADIX</span></span>|<span data-ttu-id="7767d-514">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-514">Int16</span></span>|  
|<span data-ttu-id="7767d-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="7767d-515">NULLABLE</span></span>|<span data-ttu-id="7767d-516">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-516">Int16</span></span>|  
|<span data-ttu-id="7767d-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="7767d-517">REMARKS</span></span>|<span data-ttu-id="7767d-518">String</span><span class="sxs-lookup"><span data-stu-id="7767d-518">String</span></span>|  
|<span data-ttu-id="7767d-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="7767d-519">OVERLOAD</span></span>|<span data-ttu-id="7767d-520">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-520">Int32</span></span>|  
|<span data-ttu-id="7767d-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7767d-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="7767d-522">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="7767d-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="7767d-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="7767d-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="7767d-524">ColumnName</span></span>|<span data-ttu-id="7767d-525">DataType</span><span class="sxs-lookup"><span data-stu-id="7767d-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="7767d-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="7767d-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="7767d-527">String</span><span class="sxs-lookup"><span data-stu-id="7767d-527">String</span></span>|  
|<span data-ttu-id="7767d-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="7767d-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="7767d-529">String</span><span class="sxs-lookup"><span data-stu-id="7767d-529">String</span></span>|  
|<span data-ttu-id="7767d-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="7767d-531">String</span><span class="sxs-lookup"><span data-stu-id="7767d-531">String</span></span>|  
|<span data-ttu-id="7767d-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-532">COLUMN_NAME</span></span>|<span data-ttu-id="7767d-533">String</span><span class="sxs-lookup"><span data-stu-id="7767d-533">String</span></span>|  
|<span data-ttu-id="7767d-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-534">COLUMN_TYPE</span></span>|<span data-ttu-id="7767d-535">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-535">Int16</span></span>|  
|<span data-ttu-id="7767d-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-536">DATA_TYPE</span></span>|<span data-ttu-id="7767d-537">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-537">Int16</span></span>|  
|<span data-ttu-id="7767d-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="7767d-538">TYPE_NAME</span></span>|<span data-ttu-id="7767d-539">String</span><span class="sxs-lookup"><span data-stu-id="7767d-539">String</span></span>|  
|<span data-ttu-id="7767d-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="7767d-540">COLUMN_SIZE</span></span>|<span data-ttu-id="7767d-541">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-541">Int32</span></span>|  
|<span data-ttu-id="7767d-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="7767d-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="7767d-543">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-543">Int32</span></span>|  
|<span data-ttu-id="7767d-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="7767d-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="7767d-545">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-545">Int16</span></span>|  
|<span data-ttu-id="7767d-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="7767d-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="7767d-547">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-547">Int16</span></span>|  
|<span data-ttu-id="7767d-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="7767d-548">NULLABLE</span></span>|<span data-ttu-id="7767d-549">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-549">Int16</span></span>|  
|<span data-ttu-id="7767d-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="7767d-550">REMARKS</span></span>|<span data-ttu-id="7767d-551">String</span><span class="sxs-lookup"><span data-stu-id="7767d-551">String</span></span>|  
|<span data-ttu-id="7767d-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="7767d-552">COLUMN_DEF</span></span>|<span data-ttu-id="7767d-553">String</span><span class="sxs-lookup"><span data-stu-id="7767d-553">String</span></span>|  
|<span data-ttu-id="7767d-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="7767d-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="7767d-555">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-555">Int16</span></span>|  
|<span data-ttu-id="7767d-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="7767d-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="7767d-557">Int16</span><span class="sxs-lookup"><span data-stu-id="7767d-557">Int16</span></span>|  
|<span data-ttu-id="7767d-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="7767d-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="7767d-559">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-559">Int32</span></span>|  
|<span data-ttu-id="7767d-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="7767d-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="7767d-561">Int32</span><span class="sxs-lookup"><span data-stu-id="7767d-561">Int32</span></span>|  
|<span data-ttu-id="7767d-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="7767d-562">IS_NULLABLE</span></span>|<span data-ttu-id="7767d-563">String</span><span class="sxs-lookup"><span data-stu-id="7767d-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7767d-564">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7767d-564">See also</span></span>
- [<span data-ttu-id="7767d-565">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="7767d-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
