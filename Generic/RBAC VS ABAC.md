# Role Based Access Control VS Attribute Based Access Control

Access Control (AC) is part of every application, but isn't discussed
much in classes. Truth is, there are many different methods of
implementing AC. Role Based and Attribute Basds are two major ways.

Role Based access can be simplified as a user *being* something. In a
hospital a user can be a Doctor, Patient, Manager, Nurse, Technician,
etc. Each one of these \`roles\` has access to particular parts of
different things. A Doctor might have full access to anything concerning
any patient, with the Patient only having a subset that pertain to
themselves. A Manager might have access to information relating to
Doctors and other employees.

At its core, Role Based Access Control gives each user a predefined set
of things to access, making it simple to create users.

Attribute Based access takes a different, more granular approach.
Instead of a user being a Doctor, instead they might have the
PatientView, PatientEdit accesses. A Manager would have the DoctorView,
DoctorEdit, NurseView, NurseEdit, ... accesses. A Manager might also be
a Doctor and have PatientView and PatientEdit access. Each user would
have their own set of accesses that don't have to correspond to a
particular set of accesses.

At its core, Attribute Based Access Control gives each user their own
set of things to access, allowing more freedom.

Of course you could have RBAC based off of Attributes, or predefined
Role sets in your ABAC application, which are essentially the same
thing.

So it comes down to simplicity vs freedom.
