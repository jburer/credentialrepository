# credentialrepository

A test for identification, authentication, and authorization against AWS Secrets Manager,
Azure Key Vault, and GCP Secret Manager.

There are two scenarios to allow access that I'm interested in:

1. Allow access to the service
2. Allow access to service functions
3. Allow access to all resources
4. Allow access to a specific resource

There are three scenarios to deny access that I'm interested in:

1. Deny access to the service
2. Deny access to service functions
3. Deny access to all resources
4. Deny access to a specific resource

These can be paired in the following ways:

## you have no business doing here

1. Deny access to the service

## ok, you're part of the bigger picture, but that doesn't mean you should be able to do anything

1. Allow access to the service
2. Deny access to all service functions
3. Deny access to all resources

## let's fence you in

1. Allow access to the service
2. Allow access to service functions
3. Allow access to a specific resource
4. Deny access to a specific resource

## super user

1. Allow access to the service
2. Allow access to service functions
3. Allow access to all resources

# testing, testing, 1, 2, 3

To accomplish the above you need 5 accounts:

1. No Account
2. Organizational Account
3. User Account 1
4. User Account 2
5. Administrative Account

2 resources:

1. Credential Set 1
2. Credential Set 2

And 3 permission sets:

1. User Account 1 has <i>get credential</i> scoped to Credential Set 1
1. User Account 2 has <i>get credential</i> scoped to Credential Set 2
1. Adminstrative Account has all permissions

# testing, testing, 1, 2, 3

## test 1

Non-organizational user with no account gets no where.

## test 2

Organizational Account holder can create a session, but gets access denied.

## test 3a

User Account 1 can return credentials for Credential Set 1.

## test 3b

User Account 1 cannot return credentials for Crendential Set 2.

## test 4a

User Account 2 can return credentials for Credential Set 2.

## test 4b

User Account 2 cannot return credentials for Crendential Set 1.

## test 5a

Administrative Account can return credentials for Credential Set 1.

## test 5b

Administrative Account can return credentials for Credential Set 2.
