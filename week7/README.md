# Writing and Presentation Test Week 7
## **React Context**
**Learning Objective:**\
Peserta mampu memahami dan menggunakan React Context untuk State Management

- Secara singkatnya React Context adalah sebuah cara untuk mengoper data agar dapat diakses secara global darimana saja tanpa harus memparsing props ke masing-masing komponen melalui setiap level
- Context dan Props sama saja kegunaannya tetapi dengan menggunakan context bisa dikatakan kode lebih terstruktur apalagi jika aplikasi mulai besar
- Untuk aplikasi berskala lebih besar lagi context juga memiliki kekurangannya, seperti dapat membuat penggunaan kembali komponen menjadi lebih sulit karena terlalu bersarang
- Terutama context ini dipakai ketika beberapa data harus dapat diakses oleh banyak komponen pada level-level yang berbeda

Berikut contoh kode program pemberian style pada button tanpa menggunakan context :

```
classApp extendsComponent {
    render() {
        return <Toolbar theme=”dark” />;
    }
}
function Toolbar(props) {
    return (
        <div>
            <ThemedButton theme={props.theme} />
        </div>
    );
}
classThemedButton extendsComponent {
    render() {
        return<Button theme={this.props.theme} />;
    }
}
```

Jika tidak menggunakan context, setiap tombol dalam aplikasi perlu mengetahui theme karena itu harus melewati semua komponen. Tapi dengan menggunakan context, ia dapat meneruskan nilai ke dalam pohon komponen tanpa memasukkannya ke setiap komponen secara eksplisit.Komponen apapun dapat membaca nilai pada perantara diagram komponen tanpa harus melalui setiap theme mau seberapa dalam diagram tersebut

```
const ThemeContext = React.createContext('light');

class App extends React.Component {
  render() {
    return (
      <ThemeContext.Provider value="dark">
        <Toolbar />
      </ThemeContext.Provider>
    );
  }
}

function Toolbar() {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}

class ThemedButton extends React.Component {
  static contextType = ThemeContext;
  render() {
    return <Button theme={this.context} />;
  }
}
```

## **React Testing**
**Learning Objective:**\
Peserta mampu memahami Unit Testing\
Peserta mampu membuat Unit testing dengan Jest\
Peserta mampu membuat mocking dan handle asynchronous testing dengan Jest\
Peserta mampu membuat testing untuk component React.js menggunakan RTL

- React testing merupakan sebuah library yang memungkinkan developer untuk mengetes komponen React
- Gunanya melakukan testing pada komponen adalah untuk mengurangi adanya bug pada aplikasi, meningkatkan produktivitas agar terlatih dalam mendesain dengan sebuah objektif, dan membuat kode lebih tercakup dan memudahkan jika adanya perubahan

### **Unit Testing**
- Unit testing merupakan sebuah pengujian pada suatu bagian pada aplikasi
- Tujuan dilakukan unit testing adalah untuk melakukan validasi terhadap setiap unit pada kode aplikasi agar berfungsi sesuai harapan
- Dengan unit testing perbaikan bug dapat dilakukan di awal saat development dan developer dapat memahami kode lebih baik untuk mempermudah perbaikan
- Unit testing juga dapat berfungsi sebagai dokumentasi proyek

### **Jest**
- Adalah framework pengujian JavaScript yang sederhana dan cepat dalam running, oleh karena itu ia disebut *delightful* dan *painless*
- Ketika membuat proyek React dengan perintah CRA (Create React App), pengguna akan memiliki dukungan langsung untuk library React testing dan Jest
- Jest dapat di-install dengan menggunakan :

```
npm install -g jest
```
```
npm install --save-dev jest
```

Untuk menggunakan jest dapat menggunakan seperti ini :

```
"scripts": {
    "test": "jest"
  }
```