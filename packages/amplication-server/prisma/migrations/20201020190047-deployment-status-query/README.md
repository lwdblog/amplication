# Migration `20201020190047-deployment-status-query`

This migration has been generated by Yuval Hazaz at 10/20/2020, 10:00:48 PM.
You can check out the [state of the schema](./schema.prisma) after the migration.

## Database Steps

```sql
ALTER TABLE "public"."Deployment" ADD COLUMN "statusQuery" jsonb   ,
ADD COLUMN "statusUpdatedAt" timestamp(3)   
```

## Changes

```diff
diff --git schema.prisma schema.prisma
migration 20201020131219-remove-auto-number..20201020190047-deployment-status-query
--- datamodel.dml
+++ datamodel.dml
@@ -1,7 +1,7 @@
 datasource db {
   provider = "postgresql"
-  url = "***"
+  url = "***"
 }
 generator client {
   provider = "prisma-client-js"
@@ -381,19 +381,20 @@
   Removed
 }
 model Deployment {
-  id            String               @id @default(cuid())
-  createdAt     DateTime             @default(now())
-  createdBy     User                 @relation(fields: [userId], references: [id])
-  userId        String
-  build         Build                @relation(fields: [buildId], references: [id])
-  buildId       String
-  environment   Environment          @relation(fields: [environmentId], references: [id])
-  environmentId String
-  status        EnumDeploymentStatus
-  message       String?
-  action        Action               @relation(fields: [actionId], references: [id])
-  actionId      String
+  id              String               @id @default(cuid())
+  createdAt       DateTime             @default(now())
+  createdBy       User                 @relation(fields: [userId], references: [id])
+  userId          String
+  build           Build                @relation(fields: [buildId], references: [id])
+  buildId         String
+  environment     Environment          @relation(fields: [environmentId], references: [id])
+  environmentId   String
+  status          EnumDeploymentStatus
+  message         String?
+  action          Action               @relation(fields: [actionId], references: [id])
+  actionId        String
+  statusQuery     Json?
+  statusUpdatedAt DateTime?
-
 }
```


