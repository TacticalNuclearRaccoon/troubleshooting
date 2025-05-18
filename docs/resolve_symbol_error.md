I managed to do it by myself.

Thanks to PurpleFinch form AUR, the problem was caused by some old libraries.

For overcome this problem I needed to just paste these command in the terminal.

cd /opt/resolve/libs

sudo mkdir disabled-libraries

sudo mv libglib* disabled-libraries

sudo mv libgio* disabled-libraries

sudo mv libgmodule* disabled-libraries
