<h2>Pentesting Environment</h2>
<p>This project holds a Vagrant Kali-Linux based configuration file. It sets up a penetration testing ready environment focused on CLI applications.</p>

<table>
  <tr>
    <th>Extra Features</th>
    <th>Description</th>
  </tr>
    <tr>
      <td>Oh-My-ZSH</td>
      <td>For terminal customization</td>
    </tr>
      <td>Extra Pentesting tools</td>
      <td>Sublist3r, SecLists, Gobuster, Nuclei</td>
    </tr>
    <tr>
      <td>Custom ZSH theme</td>
      <td>With custom features like continuous time & IP by interface</td>
    </tr>
</table>

<p>Custom Terminal features </p>
<table>
  <tr>
    <th>Feature</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td><code>loip</code></td>
    <td>Sets the displayed network interface. By default is <code>eth0</code></td>
    <td><code>loip=tun0</code></td>
  </tr>
</table>
<a href="https://asciinema.org/a/BHpTqyJnDB5ODTRa1kPg4mj6Y" target="_blank"><img src="https://asciinema.org/a/BHpTqyJnDB5ODTRa1kPg4mj6Y.svg" /></a>
<br>
<p>To install, just clone this repo and run Vagrant </p>
<p></p><code>git clone https://github.com/coronito1337/kali-vagrant.git ; cd kali-vagrant ; vagrant up </code></p>

<p>To use shared files from the Host to the VM, have the folders/files inside the folder where the Vagrant file is (e.g. cloned repository). </p>
<p>Vagrant automatically shares the host directory with the VM using the <code>/vagrant</code> folder</p>

