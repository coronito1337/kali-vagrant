<h2>Pentesting Theme</h2>
<p>This project aims to provide an Oh-My-ZSH pentester friendly theme, with features helpfull for the daily job.</p>

<p>Custom Terminal features </p>
<table>
  <tr>
    <th>Feature</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td><code>loint</code></td>
    <td>Sets the displayed network interface. By default is <code>eth0</code></td>
    <td><code>loint=tun0</code></td>
  </tr>
  <tr>
    <td><code>loip</code></td>
    <td>Sets the displayed IP address value. By default the loint IP will be displayed</td>
    <td><code>loip=10.10.10.1</code></td>
  </tr>
  <tr>
    <td><code>target</code></td>
    <td>Sets the target IP/Host for the whole environment.</td>
    <td><code>target=10.10.10.2 ; curl http://$target/ </code></td>
  </tr>
</table>
<a href="https://asciinema.org/a/BHpTqyJnDB5ODTRa1kPg4mj6Y" target="_blank"><img src="https://asciinema.org/a/BHpTqyJnDB5ODTRa1kPg4mj6Y.svg" /></a>
<br>
<p>To install run the following</p>
<code>wget https://raw.githubusercontent.com/coronito1337/kali-vagrant/main/pentester.zsh-theme -O ~/.oh-my-zsh/themes/pentester.zsh-theme \ 
sed -i -e 's/robbyrussell/pentester/g' ~/.zshrc
</code>
