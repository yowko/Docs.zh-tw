---
title: ODBC 結構描述集合
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: ffe80120ceffbe29c0a117cf1194860c5782be8c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365902"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="665fc-102">ODBC 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="665fc-102">ODBC Schema Collections</span></span>

<span data-ttu-id="665fc-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 ODBC 驅動程式的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="665fc-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="665fc-104">Microsoft SQL Server ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="665fc-104">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="665fc-105">Microsoft SQL Server ODBC 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="665fc-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="665fc-106">資料表</span><span class="sxs-lookup"><span data-stu-id="665fc-106">Tables</span></span>

- <span data-ttu-id="665fc-107">Indexes</span><span class="sxs-lookup"><span data-stu-id="665fc-107">Indexes</span></span>

- <span data-ttu-id="665fc-108">資料行</span><span class="sxs-lookup"><span data-stu-id="665fc-108">Columns</span></span>

- <span data-ttu-id="665fc-109">程序</span><span class="sxs-lookup"><span data-stu-id="665fc-109">Procedures</span></span>

- <span data-ttu-id="665fc-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="665fc-110">ProcedureColumns</span></span>

- <span data-ttu-id="665fc-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="665fc-111">ProcedureParameters</span></span>

- <span data-ttu-id="665fc-112">檢視</span><span class="sxs-lookup"><span data-stu-id="665fc-112">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="665fc-113">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="665fc-113">Tables and Views</span></span>

|<span data-ttu-id="665fc-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="665fc-114">ColumnName</span></span>|<span data-ttu-id="665fc-115">DataType</span><span class="sxs-lookup"><span data-stu-id="665fc-115">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="665fc-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="665fc-116">TABLE_CAT</span></span>|<span data-ttu-id="665fc-117">String</span><span class="sxs-lookup"><span data-stu-id="665fc-117">String</span></span>|
|<span data-ttu-id="665fc-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="665fc-118">TABLE_SCHEM</span></span>|<span data-ttu-id="665fc-119">String</span><span class="sxs-lookup"><span data-stu-id="665fc-119">String</span></span>|
|<span data-ttu-id="665fc-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-120">TABLE_NAME</span></span>|<span data-ttu-id="665fc-121">String</span><span class="sxs-lookup"><span data-stu-id="665fc-121">String</span></span>|
|<span data-ttu-id="665fc-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-122">TABLE_TYPE</span></span>|<span data-ttu-id="665fc-123">String</span><span class="sxs-lookup"><span data-stu-id="665fc-123">String</span></span>|
|<span data-ttu-id="665fc-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="665fc-124">REMARKS</span></span>|<span data-ttu-id="665fc-125">String</span><span class="sxs-lookup"><span data-stu-id="665fc-125">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="665fc-126">Indexes</span><span class="sxs-lookup"><span data-stu-id="665fc-126">Indexes</span></span>

|<span data-ttu-id="665fc-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="665fc-127">ColumnName</span></span>|<span data-ttu-id="665fc-128">DataType</span><span class="sxs-lookup"><span data-stu-id="665fc-128">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="665fc-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="665fc-129">TABLE_CAT</span></span>|<span data-ttu-id="665fc-130">String</span><span class="sxs-lookup"><span data-stu-id="665fc-130">String</span></span>|
|<span data-ttu-id="665fc-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="665fc-131">TABLE_SCHEM</span></span>|<span data-ttu-id="665fc-132">String</span><span class="sxs-lookup"><span data-stu-id="665fc-132">String</span></span>|
|<span data-ttu-id="665fc-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-133">TABLE_NAME</span></span>|<span data-ttu-id="665fc-134">String</span><span class="sxs-lookup"><span data-stu-id="665fc-134">String</span></span>|
|<span data-ttu-id="665fc-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="665fc-135">NON_UNIQUE</span></span>|<span data-ttu-id="665fc-136">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-136">Int16</span></span>|
|<span data-ttu-id="665fc-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="665fc-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="665fc-138">String</span><span class="sxs-lookup"><span data-stu-id="665fc-138">String</span></span>|
|<span data-ttu-id="665fc-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-139">INDEX_NAME</span></span>|<span data-ttu-id="665fc-140">String</span><span class="sxs-lookup"><span data-stu-id="665fc-140">String</span></span>|
|<span data-ttu-id="665fc-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-141">TYPE</span></span>|<span data-ttu-id="665fc-142">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-142">Int16</span></span>|
|<span data-ttu-id="665fc-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="665fc-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="665fc-144">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-144">Int16</span></span>|
|<span data-ttu-id="665fc-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-145">COLUMN_NAME</span></span>|<span data-ttu-id="665fc-146">String</span><span class="sxs-lookup"><span data-stu-id="665fc-146">String</span></span>|
|<span data-ttu-id="665fc-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="665fc-147">ASC_OR_DESC</span></span>|<span data-ttu-id="665fc-148">String</span><span class="sxs-lookup"><span data-stu-id="665fc-148">String</span></span>|
|<span data-ttu-id="665fc-149">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="665fc-149">CARDINALITY</span></span>|<span data-ttu-id="665fc-150">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-150">Int32</span></span>|
|<span data-ttu-id="665fc-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="665fc-151">PAGES</span></span>|<span data-ttu-id="665fc-152">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-152">Int32</span></span>|
|<span data-ttu-id="665fc-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="665fc-153">FILTER_CONDITION</span></span>|<span data-ttu-id="665fc-154">String</span><span class="sxs-lookup"><span data-stu-id="665fc-154">String</span></span>|
|<span data-ttu-id="665fc-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="665fc-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="665fc-156">String</span><span class="sxs-lookup"><span data-stu-id="665fc-156">String</span></span>|
|<span data-ttu-id="665fc-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="665fc-158">Byte</span><span class="sxs-lookup"><span data-stu-id="665fc-158">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="665fc-159">資料行</span><span class="sxs-lookup"><span data-stu-id="665fc-159">Columns</span></span>

|<span data-ttu-id="665fc-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="665fc-160">ColumnName</span></span>|<span data-ttu-id="665fc-161">DataType</span><span class="sxs-lookup"><span data-stu-id="665fc-161">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="665fc-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="665fc-162">TABLE_CAT</span></span>|<span data-ttu-id="665fc-163">String</span><span class="sxs-lookup"><span data-stu-id="665fc-163">String</span></span>|
|<span data-ttu-id="665fc-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="665fc-164">TABLE_SCHEM</span></span>|<span data-ttu-id="665fc-165">String</span><span class="sxs-lookup"><span data-stu-id="665fc-165">String</span></span>|
|<span data-ttu-id="665fc-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-166">TABLE_NAME</span></span>|<span data-ttu-id="665fc-167">String</span><span class="sxs-lookup"><span data-stu-id="665fc-167">String</span></span>|
|<span data-ttu-id="665fc-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-168">COLUMN_NAME</span></span>|<span data-ttu-id="665fc-169">String</span><span class="sxs-lookup"><span data-stu-id="665fc-169">String</span></span>|
|<span data-ttu-id="665fc-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-170">DATA_TYPE</span></span>|<span data-ttu-id="665fc-171">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-171">Int16</span></span>|
|<span data-ttu-id="665fc-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-172">TYPE_NAME</span></span>|<span data-ttu-id="665fc-173">String</span><span class="sxs-lookup"><span data-stu-id="665fc-173">String</span></span>|
|<span data-ttu-id="665fc-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="665fc-174">COLUMN_SIZE</span></span>|<span data-ttu-id="665fc-175">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-175">Int32</span></span>|
|<span data-ttu-id="665fc-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="665fc-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="665fc-177">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-177">Int32</span></span>|
|<span data-ttu-id="665fc-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="665fc-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="665fc-179">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-179">Int16</span></span>|
|<span data-ttu-id="665fc-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="665fc-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="665fc-181">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-181">Int16</span></span>|
|<span data-ttu-id="665fc-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="665fc-182">NULLABLE</span></span>|<span data-ttu-id="665fc-183">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-183">Int16</span></span>|
|<span data-ttu-id="665fc-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="665fc-184">REMARKS</span></span>|<span data-ttu-id="665fc-185">String</span><span class="sxs-lookup"><span data-stu-id="665fc-185">String</span></span>|
|<span data-ttu-id="665fc-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="665fc-186">COLUMN_DEF</span></span>|<span data-ttu-id="665fc-187">String</span><span class="sxs-lookup"><span data-stu-id="665fc-187">String</span></span>|
|<span data-ttu-id="665fc-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="665fc-189">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-189">Int16</span></span>|
|<span data-ttu-id="665fc-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="665fc-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="665fc-191">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-191">Int16</span></span>|
|<span data-ttu-id="665fc-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="665fc-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="665fc-193">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-193">Int32</span></span>|
|<span data-ttu-id="665fc-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="665fc-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="665fc-195">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-195">Int32</span></span>|
|<span data-ttu-id="665fc-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="665fc-196">IS_NULLABLE</span></span>|<span data-ttu-id="665fc-197">String</span><span class="sxs-lookup"><span data-stu-id="665fc-197">String</span></span>|
|<span data-ttu-id="665fc-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="665fc-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="665fc-199">String</span><span class="sxs-lookup"><span data-stu-id="665fc-199">String</span></span>|
|<span data-ttu-id="665fc-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="665fc-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="665fc-201">String</span><span class="sxs-lookup"><span data-stu-id="665fc-201">String</span></span>|
|<span data-ttu-id="665fc-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="665fc-203">Byte</span><span class="sxs-lookup"><span data-stu-id="665fc-203">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="665fc-204">程序</span><span class="sxs-lookup"><span data-stu-id="665fc-204">Procedures</span></span>

|<span data-ttu-id="665fc-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="665fc-205">ColumnName</span></span>|<span data-ttu-id="665fc-206">DataType</span><span class="sxs-lookup"><span data-stu-id="665fc-206">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="665fc-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="665fc-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="665fc-208">String</span><span class="sxs-lookup"><span data-stu-id="665fc-208">String</span></span>|
|<span data-ttu-id="665fc-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="665fc-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="665fc-210">String</span><span class="sxs-lookup"><span data-stu-id="665fc-210">String</span></span>|
|<span data-ttu-id="665fc-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="665fc-212">String</span><span class="sxs-lookup"><span data-stu-id="665fc-212">String</span></span>|
|<span data-ttu-id="665fc-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="665fc-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="665fc-214">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-214">Int32</span></span>|
|<span data-ttu-id="665fc-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="665fc-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="665fc-216">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-216">Int32</span></span>|
|<span data-ttu-id="665fc-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="665fc-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="665fc-218">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-218">Int32</span></span>|
|<span data-ttu-id="665fc-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="665fc-219">REMARKS</span></span>|<span data-ttu-id="665fc-220">String</span><span class="sxs-lookup"><span data-stu-id="665fc-220">String</span></span>|
|<span data-ttu-id="665fc-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="665fc-222">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-222">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="665fc-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="665fc-223">ProcedureColumns</span></span>

|<span data-ttu-id="665fc-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="665fc-224">ColumnName</span></span>|<span data-ttu-id="665fc-225">DataType</span><span class="sxs-lookup"><span data-stu-id="665fc-225">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="665fc-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="665fc-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="665fc-227">String</span><span class="sxs-lookup"><span data-stu-id="665fc-227">String</span></span>|
|<span data-ttu-id="665fc-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="665fc-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="665fc-229">String</span><span class="sxs-lookup"><span data-stu-id="665fc-229">String</span></span>|
|<span data-ttu-id="665fc-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="665fc-231">String</span><span class="sxs-lookup"><span data-stu-id="665fc-231">String</span></span>|
|<span data-ttu-id="665fc-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-232">COLUMN_NAME</span></span>|<span data-ttu-id="665fc-233">String</span><span class="sxs-lookup"><span data-stu-id="665fc-233">String</span></span>|
|<span data-ttu-id="665fc-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-234">COLUMN_TYPE</span></span>|<span data-ttu-id="665fc-235">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-235">Int16</span></span>|
|<span data-ttu-id="665fc-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-236">DATA_TYPE</span></span>|<span data-ttu-id="665fc-237">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-237">Int16</span></span>|
|<span data-ttu-id="665fc-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-238">TYPE_NAME</span></span>|<span data-ttu-id="665fc-239">String</span><span class="sxs-lookup"><span data-stu-id="665fc-239">String</span></span>|
|<span data-ttu-id="665fc-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="665fc-240">COLUMN_SIZE</span></span>|<span data-ttu-id="665fc-241">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-241">Int32</span></span>|
|<span data-ttu-id="665fc-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="665fc-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="665fc-243">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-243">Int32</span></span>|
|<span data-ttu-id="665fc-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="665fc-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="665fc-245">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-245">Int16</span></span>|
|<span data-ttu-id="665fc-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="665fc-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="665fc-247">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-247">Int16</span></span>|
|<span data-ttu-id="665fc-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="665fc-248">NULLABLE</span></span>|<span data-ttu-id="665fc-249">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-249">Int16</span></span>|
|<span data-ttu-id="665fc-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="665fc-250">REMARKS</span></span>|<span data-ttu-id="665fc-251">String</span><span class="sxs-lookup"><span data-stu-id="665fc-251">String</span></span>|
|<span data-ttu-id="665fc-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="665fc-252">COLUMN_DEF</span></span>|<span data-ttu-id="665fc-253">String</span><span class="sxs-lookup"><span data-stu-id="665fc-253">String</span></span>|
|<span data-ttu-id="665fc-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="665fc-255">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-255">Int16</span></span>|
|<span data-ttu-id="665fc-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="665fc-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="665fc-257">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-257">Int16</span></span>|
|<span data-ttu-id="665fc-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="665fc-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="665fc-259">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-259">Int32</span></span>|
|<span data-ttu-id="665fc-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="665fc-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="665fc-261">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-261">Int32</span></span>|
|<span data-ttu-id="665fc-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="665fc-262">IS_NULLABLE</span></span>|<span data-ttu-id="665fc-263">String</span><span class="sxs-lookup"><span data-stu-id="665fc-263">String</span></span>|
|<span data-ttu-id="665fc-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="665fc-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="665fc-265">String</span><span class="sxs-lookup"><span data-stu-id="665fc-265">String</span></span>|
|<span data-ttu-id="665fc-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="665fc-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="665fc-267">String</span><span class="sxs-lookup"><span data-stu-id="665fc-267">String</span></span>|
|<span data-ttu-id="665fc-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="665fc-269">Byte</span><span class="sxs-lookup"><span data-stu-id="665fc-269">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="665fc-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="665fc-270">ProcedureParameters</span></span>

|<span data-ttu-id="665fc-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="665fc-271">ColumnName</span></span>|<span data-ttu-id="665fc-272">DataType</span><span class="sxs-lookup"><span data-stu-id="665fc-272">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="665fc-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="665fc-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="665fc-274">String</span><span class="sxs-lookup"><span data-stu-id="665fc-274">String</span></span>|
|<span data-ttu-id="665fc-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="665fc-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="665fc-276">String</span><span class="sxs-lookup"><span data-stu-id="665fc-276">String</span></span>|
|<span data-ttu-id="665fc-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="665fc-278">String</span><span class="sxs-lookup"><span data-stu-id="665fc-278">String</span></span>|
|<span data-ttu-id="665fc-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-279">COLUMN_NAME</span></span>|<span data-ttu-id="665fc-280">String</span><span class="sxs-lookup"><span data-stu-id="665fc-280">String</span></span>|
|<span data-ttu-id="665fc-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-281">COLUMN_TYPE</span></span>|<span data-ttu-id="665fc-282">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-282">Int16</span></span>|
|<span data-ttu-id="665fc-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-283">DATA_TYPE</span></span>|<span data-ttu-id="665fc-284">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-284">Int16</span></span>|
|<span data-ttu-id="665fc-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-285">TYPE_NAME</span></span>|<span data-ttu-id="665fc-286">String</span><span class="sxs-lookup"><span data-stu-id="665fc-286">String</span></span>|
|<span data-ttu-id="665fc-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="665fc-287">COLUMN_SIZE</span></span>|<span data-ttu-id="665fc-288">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-288">Int32</span></span>|
|<span data-ttu-id="665fc-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="665fc-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="665fc-290">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-290">Int32</span></span>|
|<span data-ttu-id="665fc-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="665fc-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="665fc-292">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-292">Int16</span></span>|
|<span data-ttu-id="665fc-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="665fc-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="665fc-294">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-294">Int16</span></span>|
|<span data-ttu-id="665fc-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="665fc-295">NULLABLE</span></span>|<span data-ttu-id="665fc-296">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-296">Int16</span></span>|
|<span data-ttu-id="665fc-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="665fc-297">REMARKS</span></span>|<span data-ttu-id="665fc-298">String</span><span class="sxs-lookup"><span data-stu-id="665fc-298">String</span></span>|
|<span data-ttu-id="665fc-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="665fc-299">COLUMN_DEF</span></span>|<span data-ttu-id="665fc-300">String</span><span class="sxs-lookup"><span data-stu-id="665fc-300">String</span></span>|
|<span data-ttu-id="665fc-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="665fc-302">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-302">Int16</span></span>|
|<span data-ttu-id="665fc-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="665fc-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="665fc-304">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-304">Int16</span></span>|
|<span data-ttu-id="665fc-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="665fc-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="665fc-306">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-306">Int32</span></span>|
|<span data-ttu-id="665fc-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="665fc-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="665fc-308">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-308">Int32</span></span>|
|<span data-ttu-id="665fc-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="665fc-309">IS_NULLABLE</span></span>|<span data-ttu-id="665fc-310">String</span><span class="sxs-lookup"><span data-stu-id="665fc-310">String</span></span>|
|<span data-ttu-id="665fc-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="665fc-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="665fc-312">String</span><span class="sxs-lookup"><span data-stu-id="665fc-312">String</span></span>|
|<span data-ttu-id="665fc-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="665fc-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="665fc-314">String</span><span class="sxs-lookup"><span data-stu-id="665fc-314">String</span></span>|
|<span data-ttu-id="665fc-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="665fc-316">Byte</span><span class="sxs-lookup"><span data-stu-id="665fc-316">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="665fc-317">Microsoft Oracle ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="665fc-317">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="665fc-318">Microsoft SQL Server Oracle ODBC 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="665fc-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="665fc-319">資料表</span><span class="sxs-lookup"><span data-stu-id="665fc-319">Tables</span></span>

- <span data-ttu-id="665fc-320">資料行</span><span class="sxs-lookup"><span data-stu-id="665fc-320">Columns</span></span>

- <span data-ttu-id="665fc-321">程序</span><span class="sxs-lookup"><span data-stu-id="665fc-321">Procedures</span></span>

- <span data-ttu-id="665fc-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="665fc-322">ProcedureColumns</span></span>

- <span data-ttu-id="665fc-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="665fc-323">ProcedureParameters</span></span>

- <span data-ttu-id="665fc-324">檢視</span><span class="sxs-lookup"><span data-stu-id="665fc-324">Views</span></span>

- <span data-ttu-id="665fc-325">Indexes</span><span class="sxs-lookup"><span data-stu-id="665fc-325">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="665fc-326">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="665fc-326">Tables and Views</span></span>

|<span data-ttu-id="665fc-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="665fc-327">ColumnName</span></span>|<span data-ttu-id="665fc-328">DataType</span><span class="sxs-lookup"><span data-stu-id="665fc-328">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="665fc-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="665fc-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="665fc-330">String</span><span class="sxs-lookup"><span data-stu-id="665fc-330">String</span></span>|
|<span data-ttu-id="665fc-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="665fc-331">TABLE_OWNER</span></span>|<span data-ttu-id="665fc-332">String</span><span class="sxs-lookup"><span data-stu-id="665fc-332">String</span></span>|
|<span data-ttu-id="665fc-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-333">TABLE_NAME</span></span>|<span data-ttu-id="665fc-334">String</span><span class="sxs-lookup"><span data-stu-id="665fc-334">String</span></span>|
|<span data-ttu-id="665fc-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-335">TABLE_TYPE</span></span>|<span data-ttu-id="665fc-336">String</span><span class="sxs-lookup"><span data-stu-id="665fc-336">String</span></span>|
|<span data-ttu-id="665fc-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="665fc-337">REMARKS</span></span>|<span data-ttu-id="665fc-338">String</span><span class="sxs-lookup"><span data-stu-id="665fc-338">String</span></span>|

### <a name="columns"></a><span data-ttu-id="665fc-339">資料行</span><span class="sxs-lookup"><span data-stu-id="665fc-339">Columns</span></span>

|<span data-ttu-id="665fc-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="665fc-340">ColumnName</span></span>|<span data-ttu-id="665fc-341">DataType</span><span class="sxs-lookup"><span data-stu-id="665fc-341">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="665fc-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="665fc-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="665fc-343">String</span><span class="sxs-lookup"><span data-stu-id="665fc-343">String</span></span>|
|<span data-ttu-id="665fc-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="665fc-344">TABLE_OWNER</span></span>|<span data-ttu-id="665fc-345">String</span><span class="sxs-lookup"><span data-stu-id="665fc-345">String</span></span>|
|<span data-ttu-id="665fc-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-346">TABLE_NAME</span></span>|<span data-ttu-id="665fc-347">String</span><span class="sxs-lookup"><span data-stu-id="665fc-347">String</span></span>|
|<span data-ttu-id="665fc-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-348">COLUMN_NAME</span></span>|<span data-ttu-id="665fc-349">String</span><span class="sxs-lookup"><span data-stu-id="665fc-349">String</span></span>|
|<span data-ttu-id="665fc-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-350">DATA_TYPE</span></span>|<span data-ttu-id="665fc-351">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-351">Int16</span></span>|
|<span data-ttu-id="665fc-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-352">TYPE_NAME</span></span>|<span data-ttu-id="665fc-353">String</span><span class="sxs-lookup"><span data-stu-id="665fc-353">String</span></span>|
|<span data-ttu-id="665fc-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="665fc-354">PRECISION</span></span>|<span data-ttu-id="665fc-355">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-355">Int32</span></span>|
|<span data-ttu-id="665fc-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="665fc-356">LENGTH</span></span>|<span data-ttu-id="665fc-357">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-357">Int32</span></span>|
|<span data-ttu-id="665fc-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="665fc-358">SCALE</span></span>|<span data-ttu-id="665fc-359">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-359">Int16</span></span>|
|<span data-ttu-id="665fc-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="665fc-360">RADIX</span></span>|<span data-ttu-id="665fc-361">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-361">Int16</span></span>|
|<span data-ttu-id="665fc-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="665fc-362">NULLABLE</span></span>|<span data-ttu-id="665fc-363">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-363">Int16</span></span>|
|<span data-ttu-id="665fc-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="665fc-364">REMARKS</span></span>|<span data-ttu-id="665fc-365">String</span><span class="sxs-lookup"><span data-stu-id="665fc-365">String</span></span>|
|<span data-ttu-id="665fc-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="665fc-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="665fc-367">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-367">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="665fc-368">程序</span><span class="sxs-lookup"><span data-stu-id="665fc-368">Procedures</span></span>

|<span data-ttu-id="665fc-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="665fc-369">ColumnName</span></span>|<span data-ttu-id="665fc-370">DataType</span><span class="sxs-lookup"><span data-stu-id="665fc-370">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="665fc-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="665fc-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="665fc-372">String</span><span class="sxs-lookup"><span data-stu-id="665fc-372">String</span></span>|
|<span data-ttu-id="665fc-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="665fc-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="665fc-374">String</span><span class="sxs-lookup"><span data-stu-id="665fc-374">String</span></span>|
|<span data-ttu-id="665fc-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="665fc-376">String</span><span class="sxs-lookup"><span data-stu-id="665fc-376">String</span></span>|
|<span data-ttu-id="665fc-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="665fc-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="665fc-378">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-378">Int16</span></span>|
|<span data-ttu-id="665fc-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="665fc-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="665fc-380">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-380">Int16</span></span>|
|<span data-ttu-id="665fc-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="665fc-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="665fc-382">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-382">Int16</span></span>|
|<span data-ttu-id="665fc-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="665fc-383">REMARKS</span></span>|<span data-ttu-id="665fc-384">String</span><span class="sxs-lookup"><span data-stu-id="665fc-384">String</span></span>|
|<span data-ttu-id="665fc-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="665fc-386">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-386">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="665fc-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="665fc-387">ProcedureColumns</span></span>

|<span data-ttu-id="665fc-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="665fc-388">ColumnName</span></span>|<span data-ttu-id="665fc-389">DataType</span><span class="sxs-lookup"><span data-stu-id="665fc-389">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="665fc-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="665fc-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="665fc-391">String</span><span class="sxs-lookup"><span data-stu-id="665fc-391">String</span></span>|
|<span data-ttu-id="665fc-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="665fc-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="665fc-393">String</span><span class="sxs-lookup"><span data-stu-id="665fc-393">String</span></span>|
|<span data-ttu-id="665fc-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="665fc-395">String</span><span class="sxs-lookup"><span data-stu-id="665fc-395">String</span></span>|
|<span data-ttu-id="665fc-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-396">COLUMN_NAME</span></span>|<span data-ttu-id="665fc-397">String</span><span class="sxs-lookup"><span data-stu-id="665fc-397">String</span></span>|
|<span data-ttu-id="665fc-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-398">COLUMN_TYPE</span></span>|<span data-ttu-id="665fc-399">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-399">Int16</span></span>|
|<span data-ttu-id="665fc-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-400">DATA_TYPE</span></span>|<span data-ttu-id="665fc-401">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-401">Int16</span></span>|
|<span data-ttu-id="665fc-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-402">TYPE_NAME</span></span>|<span data-ttu-id="665fc-403">String</span><span class="sxs-lookup"><span data-stu-id="665fc-403">String</span></span>|
|<span data-ttu-id="665fc-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="665fc-404">PRECISION</span></span>|<span data-ttu-id="665fc-405">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-405">Int32</span></span>|
|<span data-ttu-id="665fc-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="665fc-406">LENGTH</span></span>|<span data-ttu-id="665fc-407">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-407">Int32</span></span>|
|<span data-ttu-id="665fc-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="665fc-408">SCALE</span></span>|<span data-ttu-id="665fc-409">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-409">Int16</span></span>|
|<span data-ttu-id="665fc-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="665fc-410">RADIX</span></span>|<span data-ttu-id="665fc-411">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-411">Int16</span></span>|
|<span data-ttu-id="665fc-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="665fc-412">NULLABLE</span></span>|<span data-ttu-id="665fc-413">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-413">Int16</span></span>|
|<span data-ttu-id="665fc-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="665fc-414">REMARKS</span></span>|<span data-ttu-id="665fc-415">String</span><span class="sxs-lookup"><span data-stu-id="665fc-415">String</span></span>|
|<span data-ttu-id="665fc-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="665fc-416">OVERLOAD</span></span>|<span data-ttu-id="665fc-417">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-417">Int32</span></span>|
|<span data-ttu-id="665fc-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="665fc-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="665fc-419">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-419">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="665fc-420">Microsoft Jet ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="665fc-420">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="665fc-421">除了通用結構描述集合之外，Microsoft Jet ODBC 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="665fc-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="665fc-422">資料表</span><span class="sxs-lookup"><span data-stu-id="665fc-422">Tables</span></span>

- <span data-ttu-id="665fc-423">Indexes</span><span class="sxs-lookup"><span data-stu-id="665fc-423">Indexes</span></span>

- <span data-ttu-id="665fc-424">資料行</span><span class="sxs-lookup"><span data-stu-id="665fc-424">Columns</span></span>

- <span data-ttu-id="665fc-425">程序</span><span class="sxs-lookup"><span data-stu-id="665fc-425">Procedures</span></span>

- <span data-ttu-id="665fc-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="665fc-426">ProcedureColumns</span></span>

- <span data-ttu-id="665fc-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="665fc-427">ProcedureParameters</span></span>

- <span data-ttu-id="665fc-428">檢視</span><span class="sxs-lookup"><span data-stu-id="665fc-428">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="665fc-429">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="665fc-429">Tables and Views</span></span>

|<span data-ttu-id="665fc-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="665fc-430">ColumnName</span></span>|<span data-ttu-id="665fc-431">DataType</span><span class="sxs-lookup"><span data-stu-id="665fc-431">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="665fc-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="665fc-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="665fc-433">String</span><span class="sxs-lookup"><span data-stu-id="665fc-433">String</span></span>|
|<span data-ttu-id="665fc-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="665fc-434">TABLE_OWNER</span></span>|<span data-ttu-id="665fc-435">String</span><span class="sxs-lookup"><span data-stu-id="665fc-435">String</span></span>|
|<span data-ttu-id="665fc-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-436">TABLE_NAME</span></span>|<span data-ttu-id="665fc-437">String</span><span class="sxs-lookup"><span data-stu-id="665fc-437">String</span></span>|
|<span data-ttu-id="665fc-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-438">TABLE_TYPE</span></span>|<span data-ttu-id="665fc-439">String</span><span class="sxs-lookup"><span data-stu-id="665fc-439">String</span></span>|
|<span data-ttu-id="665fc-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="665fc-440">REMARKS</span></span>|<span data-ttu-id="665fc-441">String</span><span class="sxs-lookup"><span data-stu-id="665fc-441">String</span></span>|

### <a name="columns"></a><span data-ttu-id="665fc-442">資料行</span><span class="sxs-lookup"><span data-stu-id="665fc-442">Columns</span></span>

|<span data-ttu-id="665fc-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="665fc-443">ColumnName</span></span>|<span data-ttu-id="665fc-444">DataType</span><span class="sxs-lookup"><span data-stu-id="665fc-444">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="665fc-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="665fc-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="665fc-446">String</span><span class="sxs-lookup"><span data-stu-id="665fc-446">String</span></span>|
|<span data-ttu-id="665fc-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="665fc-447">TABLE_OWNER</span></span>|<span data-ttu-id="665fc-448">String</span><span class="sxs-lookup"><span data-stu-id="665fc-448">String</span></span>|
|<span data-ttu-id="665fc-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-449">TABLE_NAME</span></span>|<span data-ttu-id="665fc-450">String</span><span class="sxs-lookup"><span data-stu-id="665fc-450">String</span></span>|
|<span data-ttu-id="665fc-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-451">COLUMN_NAME</span></span>|<span data-ttu-id="665fc-452">String</span><span class="sxs-lookup"><span data-stu-id="665fc-452">String</span></span>|
|<span data-ttu-id="665fc-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-453">DATA_TYPE</span></span>|<span data-ttu-id="665fc-454">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-454">Int16</span></span>|
|<span data-ttu-id="665fc-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-455">TYPE_NAME</span></span>|<span data-ttu-id="665fc-456">String</span><span class="sxs-lookup"><span data-stu-id="665fc-456">String</span></span>|
|<span data-ttu-id="665fc-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="665fc-457">PRECISION</span></span>|<span data-ttu-id="665fc-458">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-458">Int32</span></span>|
|<span data-ttu-id="665fc-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="665fc-459">LENGTH</span></span>|<span data-ttu-id="665fc-460">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-460">Int32</span></span>|
|<span data-ttu-id="665fc-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="665fc-461">SCALE</span></span>|<span data-ttu-id="665fc-462">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-462">Int16</span></span>|
|<span data-ttu-id="665fc-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="665fc-463">RADIX</span></span>|<span data-ttu-id="665fc-464">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-464">Int16</span></span>|
|<span data-ttu-id="665fc-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="665fc-465">NULLABLE</span></span>|<span data-ttu-id="665fc-466">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-466">Int16</span></span>|
|<span data-ttu-id="665fc-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="665fc-467">REMARKS</span></span>|<span data-ttu-id="665fc-468">String</span><span class="sxs-lookup"><span data-stu-id="665fc-468">String</span></span>|
|<span data-ttu-id="665fc-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="665fc-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="665fc-470">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-470">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="665fc-471">程序</span><span class="sxs-lookup"><span data-stu-id="665fc-471">Procedures</span></span>

|<span data-ttu-id="665fc-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="665fc-472">ColumnName</span></span>|<span data-ttu-id="665fc-473">DataType</span><span class="sxs-lookup"><span data-stu-id="665fc-473">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="665fc-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="665fc-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="665fc-475">String</span><span class="sxs-lookup"><span data-stu-id="665fc-475">String</span></span>|
|<span data-ttu-id="665fc-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="665fc-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="665fc-477">String</span><span class="sxs-lookup"><span data-stu-id="665fc-477">String</span></span>|
|<span data-ttu-id="665fc-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="665fc-479">String</span><span class="sxs-lookup"><span data-stu-id="665fc-479">String</span></span>|
|<span data-ttu-id="665fc-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="665fc-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="665fc-481">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-481">Int16</span></span>|
|<span data-ttu-id="665fc-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="665fc-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="665fc-483">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-483">Int16</span></span>|
|<span data-ttu-id="665fc-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="665fc-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="665fc-485">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-485">Int16</span></span>|
|<span data-ttu-id="665fc-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="665fc-486">REMARKS</span></span>|<span data-ttu-id="665fc-487">String</span><span class="sxs-lookup"><span data-stu-id="665fc-487">String</span></span>|
|<span data-ttu-id="665fc-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="665fc-489">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-489">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="665fc-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="665fc-490">ProcedureColumns</span></span>

|<span data-ttu-id="665fc-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="665fc-491">ColumnName</span></span>|<span data-ttu-id="665fc-492">DataType</span><span class="sxs-lookup"><span data-stu-id="665fc-492">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="665fc-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="665fc-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="665fc-494">String</span><span class="sxs-lookup"><span data-stu-id="665fc-494">String</span></span>|
|<span data-ttu-id="665fc-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="665fc-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="665fc-496">String</span><span class="sxs-lookup"><span data-stu-id="665fc-496">String</span></span>|
|<span data-ttu-id="665fc-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="665fc-498">String</span><span class="sxs-lookup"><span data-stu-id="665fc-498">String</span></span>|
|<span data-ttu-id="665fc-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-499">COLUMN_NAME</span></span>|<span data-ttu-id="665fc-500">String</span><span class="sxs-lookup"><span data-stu-id="665fc-500">String</span></span>|
|<span data-ttu-id="665fc-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-501">COLUMN_TYPE</span></span>|<span data-ttu-id="665fc-502">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-502">Int16</span></span>|
|<span data-ttu-id="665fc-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-503">DATA_TYPE</span></span>|<span data-ttu-id="665fc-504">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-504">Int16</span></span>|
|<span data-ttu-id="665fc-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-505">TYPE_NAME</span></span>|<span data-ttu-id="665fc-506">String</span><span class="sxs-lookup"><span data-stu-id="665fc-506">String</span></span>|
|<span data-ttu-id="665fc-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="665fc-507">PRECISION</span></span>|<span data-ttu-id="665fc-508">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-508">Int32</span></span>|
|<span data-ttu-id="665fc-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="665fc-509">LENGTH</span></span>|<span data-ttu-id="665fc-510">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-510">Int32</span></span>|
|<span data-ttu-id="665fc-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="665fc-511">SCALE</span></span>|<span data-ttu-id="665fc-512">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-512">Int16</span></span>|
|<span data-ttu-id="665fc-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="665fc-513">RADIX</span></span>|<span data-ttu-id="665fc-514">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-514">Int16</span></span>|
|<span data-ttu-id="665fc-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="665fc-515">NULLABLE</span></span>|<span data-ttu-id="665fc-516">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-516">Int16</span></span>|
|<span data-ttu-id="665fc-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="665fc-517">REMARKS</span></span>|<span data-ttu-id="665fc-518">String</span><span class="sxs-lookup"><span data-stu-id="665fc-518">String</span></span>|
|<span data-ttu-id="665fc-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="665fc-519">OVERLOAD</span></span>|<span data-ttu-id="665fc-520">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-520">Int32</span></span>|
|<span data-ttu-id="665fc-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="665fc-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="665fc-522">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-522">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="665fc-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="665fc-523">ProcedureParameters</span></span>

|<span data-ttu-id="665fc-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="665fc-524">ColumnName</span></span>|<span data-ttu-id="665fc-525">DataType</span><span class="sxs-lookup"><span data-stu-id="665fc-525">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="665fc-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="665fc-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="665fc-527">String</span><span class="sxs-lookup"><span data-stu-id="665fc-527">String</span></span>|
|<span data-ttu-id="665fc-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="665fc-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="665fc-529">String</span><span class="sxs-lookup"><span data-stu-id="665fc-529">String</span></span>|
|<span data-ttu-id="665fc-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="665fc-531">String</span><span class="sxs-lookup"><span data-stu-id="665fc-531">String</span></span>|
|<span data-ttu-id="665fc-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-532">COLUMN_NAME</span></span>|<span data-ttu-id="665fc-533">String</span><span class="sxs-lookup"><span data-stu-id="665fc-533">String</span></span>|
|<span data-ttu-id="665fc-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-534">COLUMN_TYPE</span></span>|<span data-ttu-id="665fc-535">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-535">Int16</span></span>|
|<span data-ttu-id="665fc-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-536">DATA_TYPE</span></span>|<span data-ttu-id="665fc-537">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-537">Int16</span></span>|
|<span data-ttu-id="665fc-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="665fc-538">TYPE_NAME</span></span>|<span data-ttu-id="665fc-539">String</span><span class="sxs-lookup"><span data-stu-id="665fc-539">String</span></span>|
|<span data-ttu-id="665fc-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="665fc-540">COLUMN_SIZE</span></span>|<span data-ttu-id="665fc-541">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-541">Int32</span></span>|
|<span data-ttu-id="665fc-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="665fc-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="665fc-543">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-543">Int32</span></span>|
|<span data-ttu-id="665fc-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="665fc-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="665fc-545">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-545">Int16</span></span>|
|<span data-ttu-id="665fc-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="665fc-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="665fc-547">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-547">Int16</span></span>|
|<span data-ttu-id="665fc-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="665fc-548">NULLABLE</span></span>|<span data-ttu-id="665fc-549">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-549">Int16</span></span>|
|<span data-ttu-id="665fc-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="665fc-550">REMARKS</span></span>|<span data-ttu-id="665fc-551">String</span><span class="sxs-lookup"><span data-stu-id="665fc-551">String</span></span>|
|<span data-ttu-id="665fc-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="665fc-552">COLUMN_DEF</span></span>|<span data-ttu-id="665fc-553">String</span><span class="sxs-lookup"><span data-stu-id="665fc-553">String</span></span>|
|<span data-ttu-id="665fc-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="665fc-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="665fc-555">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-555">Int16</span></span>|
|<span data-ttu-id="665fc-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="665fc-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="665fc-557">Int16</span><span class="sxs-lookup"><span data-stu-id="665fc-557">Int16</span></span>|
|<span data-ttu-id="665fc-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="665fc-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="665fc-559">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-559">Int32</span></span>|
|<span data-ttu-id="665fc-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="665fc-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="665fc-561">Int32</span><span class="sxs-lookup"><span data-stu-id="665fc-561">Int32</span></span>|
|<span data-ttu-id="665fc-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="665fc-562">IS_NULLABLE</span></span>|<span data-ttu-id="665fc-563">String</span><span class="sxs-lookup"><span data-stu-id="665fc-563">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="665fc-564">另請參閱</span><span class="sxs-lookup"><span data-stu-id="665fc-564">See also</span></span>

- [<span data-ttu-id="665fc-565">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="665fc-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
