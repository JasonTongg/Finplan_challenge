// TES LOGIKA
// NO. 1
let n = prompt('No.1, Input jumlah angka: ');
let nCopy = n;
let count = 0;
let result1 = [];

while (nCopy > 0) {
  count++;
  if (count % 3 === 0 && count % 7 === 0) {
    result1 = [...result1, 'Z'];
    nCopy--;
  } else if (count % 3 === 0 || count % 7 === 0) {
    result1 = [...result1, count];
    nCopy--;
  }
}
console.log('No. 1');
console.log('Input: ' + n);
console.log('Output: ' + result1);

// NO. 2
let kalimat = prompt('No.2, Input kalimat: ');
let kalimatCopy = kalimat;
let result2 = [];
let findGajah, findHarimau, findSerigala;

while (true) {
  findGajah = kalimatCopy.toLowerCase().indexOf('sang gajah');
  findSerigala = kalimatCopy.toLowerCase().indexOf('serigala');
  findHarimau = kalimatCopy.toLowerCase().indexOf('harimau');

  if (findGajah !== -1) {
    result2 = [...result2, {value: 'sang gajah', index: findGajah}];
    kalimatCopy =
      kalimatCopy.substring(0, findGajah) +
      '*' +
      kalimatCopy.substring(findGajah + 1);
  }
  if (findSerigala !== -1) {
    result2 = [...result2, {value: 'serigala', index: findSerigala}];
    kalimatCopy =
      kalimatCopy.substring(0, findSerigala) +
      '*' +
      kalimatCopy.substring(findSerigala + 1);
  }
  if (findHarimau !== -1) {
    result2 = [...result2, {value: 'harimau', index: findHarimau}];
    kalimatCopy =
      kalimatCopy.substring(0, findHarimau) +
      '*' +
      kalimatCopy.substring(findHarimau + 1);
  }

  if (findGajah === -1 && findHarimau === -1 && findSerigala === -1) {
    result2.sort((a, b) => a.index - b.index);
    result2 = result2.map((item) => item.value);

    console.log('No. 2');
    console.log('Input: ' + kalimat);
    console.log('Output: ' + result2);
    break;
  }
}

// NO. 3
let password = prompt('No.3, Input password: ');
console.log('No. 3');
console.log('Input: ' + password);
console.log('Output: ');

if (password.length < 8) console.log('Kata sandi minimal 8 karakter');
else if (password.length > 32) console.log('Kata sandi maksimal 32 karakter');
else if (!isNaN(password.charAt(0)))
  console.log('Karakter awal tidak boleh angka');
else if (/[0-9]/.test(password) === false) console.log('Harus memiliki angka');
else if (
  password === password.toUpperCase() ||
  password === password.toLowerCase()
)
  console.log('Harus memiliki huruf kapital dan huruf kecil');
else console.log('Kata sandi valid');

// NO. 4
let arr = JSON.parse(prompt('No.4, Input arr contoh: "[8, 6, 7, 12]": '));
for (let i = Math.min(...arr) + 1; i < Math.max(...arr); i++) {
  let find = arr.find((item) => item === i);
  if (find === undefined) {
    console.log('No. 4');
    console.log('Input: ' + arr);
    console.log('Output: ' + i);
    break;
  }
}

// NO. 5
let m = prompt('No.5, Input panjang persegi(ganjil): ');
let pattern = [m - 3, 0];
let row = [];
let col = [];

for (let i = 0; i < m; i++) {
  row = [...row, 'X'];
}
col = [...col, row];
row = [];
for (let i = 0; i < m - 2; i++) {
  row = [...row, 'X'];
  for (let k = 0; k < pattern[0]; k++) {
    row = [...row, 'O'];
  }
  row = [...row, 'X'];
  for (let k = 0; k < pattern[1]; k++) {
    row = [...row, 'O'];
  }
  row = [...row, 'X'];
  pattern[0] -= 1;
  pattern[1] += 1;
  col = [...col, row];
  row = [];
}
for (let i = 0; i < m; i++) {
  row = [...row, 'X'];
}
col = [...col, row];
row = [];

console.log('No. 5');
console.log('Input: ' + m);
console.log('Output: ');
console.log(col);
