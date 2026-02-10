# nix_modules

This is a repo of nixos modules, for now it'll just have the nordvpn module and move from there.  I've just dumped things in the main dir but i'll break things out into sub directories when I have some downtime.


## Nordvpn

### How to use

* Create a file in your nix config folder called `nordvpn.nix` and paste the contents there
* In your `configuration.nix` add it to your imports

```nix
  imports =
    [ # Include the results of the hardware scan.
      ./hardware-configuration.nix
      ./nordvpn-module.nix
    ];
```
* Run `sudo nixos-rebuild switch` and it will install the package, then just login and start using!


### Updating the package

I'll try and keep this up to date, but if you need to do it yourself on line 27 you'll need to change the version.  You can find the latest version of the deb files [here](https://repo.nordvpn.com/deb/nordvpn/debian/pool/main/n/nordvpn/) get the version number i.e. 4.1.2 and replace the version

Make the hash in line 34 an empty string `""` and then do `sudo nixos-rebuild switch` it will fail due to the hash being in correct, paste the correct hash into the string and then re-run `sudo nixos-rebuild switch` and it should build

### Troubleshooting

I'm still learning nixos language so my understanding of this is very low (I'm trying, lol) but I'll do my best effort to take a look at what I can.
