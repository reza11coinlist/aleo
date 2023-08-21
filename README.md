# aleo

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

source $HOME/.cargo/env

rustup install stable

rustup update stable

rustup default stable

git clone https://github.com/AleoHQ/leo
cd leo (enter)

apt install clang gcc libssl-dev pkg-config     (y+enter)

cargo install --path .

git clone https://github.com/AleoHQ/snarkOS.git --depth 1
cd snarkOS    (enter)

./build_ubuntu.sh

cargo install --path .




------------------------------------------------------------------

cd $HOME

mkdir demo_deploy_Leo_app && cd demo_deploy_Leo_app

WALLETADDRESS=""

APPNAME=helloworld_"${WALLETADDRESS:4:6}"

leo new "${APPNAME}"

PATHTOAPP=$(realpath -q $APPNAME)

cd $PATHTOAPP && cd ..

PRIVATEKEY=""

RECORD=""

snarkos developer deploy "${APPNAME}.aleo" --private-key "${PRIVATEKEY}" --query "https://vm.aleo.org/api" --path "./${APPNAME}/build/" --broadcast "https://vm.aleo.org/api/testnet3/transaction/broadcast" --fee 1000000 --record "${RECORD}"
