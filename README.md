<b> Puppet-moduli harjoitus </b>

Harjoituksessa teen ja testaan puppet modulin. Harjoitus suoritetaan ubuntu 14.04 live usb tikulla.

<b> Asennus </b>

Ensin asennan puppetin käskyillä:

$ sudo apt-get update
$ sudo apt-get install puppet

Sitten loin puppet kansion käskyllä

$ mkdir puppet

Johon loin modules kansion, ja sinne test_module kansion, ja sen sisälle manifests kansion

$ mkdir -p modules/test/manifests/

Kyseiseen kansioon luon tiedoston init.pp käskyllä

$nano modules/test/manifests/init.pp

Ja sinne kirjoitan seuraavan koodi pätkän.

class test {
        file { '/tmp/testModule':
            content => "Test test test\n"
        }
}

Seuraavaksi kokeilin ajaa modulin käskyllä

$ puppet apply --modulepath modules/ -e 'class {"test":}'

Ja sitten annoin seuraavat käskyt kokeillakseni sen toimintaa

$ ls /tmp/test_moduleModule/tmp/test_moduleModule

$ cat /tmp/test_moduleModule

komentorivi toisti "Test test test" eli se toimii kuten pitäisi.

<b> Modulin luonti </b>

Harjoitukseksi luon modulin joka asentaa nethackin.

ensin luon tarvittavat kansiot

$ mkdir -p modules/nethack/manifests/

ja sinne init.pp tiedoston

ja sinne koodi

class nethack {

package { 'nethack-x11':
        ensure => installed,

        }

}

sitten komentoriviin käsky 

$ puppet apply --modulepath modules/ -e 'class {"nethack":}'

jonka jälkeen yritin käynnistää komentoriviltä nethackin joka käynnistyi.
