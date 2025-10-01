#include <Magick++.h>
#include <iostream>
#include <filesystem>

using namespace std;
using namespace Magick;

int main(int argc, char *argv[])
{
    InitializeMagick(*argv);

    const string inputPath = "input.jpg";

    // Vérification de l'existence du fichier
    if (!filesystem::exists(inputPath)) {
        cerr << "Erreur : le fichier '" << inputPath << "' est introuvable." << endl;
        return 1;
    }

    try {
        // Lecture de l'image originale
        Image original(inputPath);

        // Redimensionnement
        Image resized = original;
        resized.resize(Geometry(800, 600));
        resized.write("output.jpg");
        cout << "✔ Image redimensionnée → output.jpg" << endl;

        // Flou
        Image blurred = original;
        blurred.blur(5.0, 3.0);
        blurred.write("blurred.jpg");
        cout << "✔ Image floutée → blurred.jpg" << endl;

        // Détection des contours
        Image edged = original;
        edged.edge(0.5);
        edged.write("edged.jpg");
        cout << "✔ Contours détectés → edged.jpg" << endl;

        // Relief
        Image embossed = original;
        embossed.emboss();
        embossed.write("embossed.jpg");
        cout << "✔ Image en relief → embossed.jpg" << endl;

        // Netteté
        Image sharpened = original;
        sharpened.sharpen(1.5);
        sharpened.write("sharpened.jpg");
        cout << "✔ Image accentuée → sharpened.jpg" << endl;

    } catch (Exception &error_) {
        cerr << "Exception capturée : " << error_.what() << endl;
        return 1;
    }

    return 0;
}
