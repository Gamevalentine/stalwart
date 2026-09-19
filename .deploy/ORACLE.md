# Oracle Always Free deployment

This template is intended for an Oracle Cloud Always Free VM and does not require storing the project on a local PC.

## Recommended Always Free VM

- Home region only
- Ubuntu
- VM.Standard.A1.Flex
- 1 OCPU and 6 GB RAM (well within the Always Free allowance)
- Default boot volume
- Public IPv4 address

Stalwart's official Docker image is multi-architecture and supports arm64, so it can run on OCI Ampere A1.

## During instance creation

Open Advanced options and paste the contents of `oracle-cloud-init.yaml` into the cloud-init / user-data field.

Before launching, replace:

`CHANGE_ME_BEFORE_LAUNCH`

with a strong temporary password chosen by the account owner. Do not commit that password to GitHub.

## Network ingress

Temporarily allow TCP 8080 for the Stalwart setup wizard. For production mail, the needed ports depend on which protocols are enabled; commonly 443, 25, 465, 587, 993 and optionally the other ports in the Compose file.

## First login

When the VM is ready, open:

`http://PUBLIC_IP:8080/admin`

Username: `admin`

Password: the temporary password entered in cloud-init.

Complete the Stalwart wizard using the intended hostname and domain. After a permanent administrator is created and HTTPS is working, remove the recovery credential and close the temporary HTTP setup listener.

## Important OCI mail limitation

New OCI tenancies block outbound TCP port 25 by default. Stalwart can still be installed and receive mail, but direct outbound SMTP delivery will require an OCI exemption or an SMTP relay on a supported submission port.
